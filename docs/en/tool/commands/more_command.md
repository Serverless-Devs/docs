# Extensive instruction capability

Extensive instruction is a very interesting concept and is rare in many command line tools.

Traditionally, or in general, the command line tool we have seen is a tool developer who has already defined various instructions. However, we have fully released this capability in the Serverless Devs Tool.

In the official provided `config `, `init `, `set `, `search `, `platform `in addition to instructions, we provide an extensive instruction, that is, an instruction defined by the component developer. In fact, the usage is as follows.

For example, when we have a project that uses `FC `components:

```yaml
MyFunctionDemo:
  Component: fc
  Provider: alibaba
  Properties:
    Region: cn-hangzhou
    Service:
      Name: abc
      Description: welcome to use the serverlesnode tool.
    Function:
      Name: serverless_demo
      Description: This is a test case of Nodejs10
      CodeUri: ./
      Handler: index.handler
      MemorySize: 512
      Runtime: nodejs10
```

At this point, we proceed under the Project Directory. `s -h `we can see that a new project has been added `MyFunctionDemo `instructions:
[](https://images.serverlessfans.com/s-tool/zh/s-command-help-1.jpg)

At this point, when we execute `s MyFunctionDemo -h `at that time, we can see some methods under our project:
[](https://images.serverlessfans.com/s-tool/zh/s-command-help-2.jpg)

At this point, we can execute the corresponding instructions and perform different operations, such `s MyFunctionDemo deploy `deploy the project.

Of course, in addition, we can also directly carry out `s deploy `. Direct execution `s deploy `the system calls its components one by one in the deployment order `deploy `method.

For example, in a Yaml file, you have three projects:

```yaml
Project1:
  Component: a
  Provider: alibaba
  Properties: test

Project2:
  Component: b
  Provider: alibaba
  Properties: test

Project3:
  Component: c
  Provider: alibaba
  Properties: test
```

The component methods corresponding to these three projects:

- Project1: a component is used. Component a uses the deploy method.
- Project2: Component B is used. Component B does not have the deploy method.
- Project3: Component c is used. Use the deploy method for component c.

If I execute at this moment `s Project1 deploy `the system only executes the deploy method of the component on which Project1 depends.
If I execute `s Project2 deploy `because component B does not have the deploy method, the system reports an error.

When I want to do a batch operation, I can do it directly. `s deploy `at this moment, the system will:

1. Analyze the deployment sequence of Project1,Project2, and project3.
2. deploy Project1. Component a has the deploy method, so no errors or warnings are reported;
3. When deploying Project2, component B throws a warning message because it does not have a deploy method, but does not terminate the process;
4. deploy Project3. The c component has the deploy method, so no errors or warnings are reported;
5. After the deployment is completed, all summary information is generated;

Because the Serverless Devs Tool is a component-based Tool, we believe that each component may have a different approach, such as the function compute component using the logs,invoke, and deploy methods, the components of a static website may have methods such as deploy,remove, and update. Therefore, we can transparently transmit the instructions of the components to the outside of the tool to make it clear to users. On the one hand, we can provide more flexibility for the components, it enables developers to complete more capabilities more easily, easily and freely, and on the other hand, it allows users to use a certain function and a certain capability more pertinently.

