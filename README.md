# DOCTALES Graal

![GraalVM](https://raw.githubusercontent.com/oracle/graal/master/.github/assets/logo_320x64.svg)

DOCTALES Graal is a simple wrapper DITA-OT plugin, which provides the Graal VM, which is needed to execute JavaScript in Apache Ant.

GraalVM is a high-performance JDK distribution designed to accelerate the execution of applications written in Java and other JVM languages along with support for JavaScript, Ruby, Python, and a number of other popular languages.


## Installation

Install this plugin with the `dita` command.

```bash
dita install https://github.com/doctales/org.doctales.graal/archive/refs/heads/main.zip
```


## Usage

You can use the Apache Ant **`[<script>](https://ant.apache.org/manual/Tasks/script.html)`** task.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project name="MyProject" basedir="." default="main">

  <target name="main">
    <script language="javascript"> <![CDATA[
        // create and use a Task via Ant API
        echo = MyProject.createTask("echo");
        echo.setMessage("Hello World!");
        echo.perform();
      }
    ]]></script>
  </target>

</project>
```

As an alternative, you can also use the **`[<scriptdef>](https://ant.apache.org/manual/Tasks/scriptdef.html)`** task to create custom Ant tasks.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project name="MyProject" basedir="." default="main">

  <scriptdef name="custom-echo" language="javascript">
    <attribute name="msg"/>
    <![CDATA[
      self.log(attributes.get("msg"));
    ]]>
  </scriptdef>

  <target name="main">
    <custom-echo msg="Hello World!"/>
  </target>
  
</project>
```


## License

GraalVM Community Edition is open source and distributed under [version 2 of the GNU General Public License with the “Classpath” Exception](LICENSE), which are the same terms as for Java. The licenses of the individual GraalVM components are generally derivative of the license of a particular language (see the table below). GraalVM Community is free to use for any purpose - no strings attached.

Component(s) | License
------------ | -------------
[Espresso](espresso/LICENSE) | GPL 2
[GraalVM Compiler](compiler/LICENSE.md), [SubstrateVM](substratevm/LICENSE), [Tools](tools/LICENSE), [VM](vm/LICENSE_GRAALVM_CE) | GPL 2 with Classpath Exception
[GraalVM SDK](sdk/LICENSE.md), [GraalWasm](wasm/LICENSE), [Truffle Framework](truffle/LICENSE.md), [TRegex](regex/LICENSE.md) | Universal Permissive License
[Sulong](sulong/LICENSE) | 3-clause BSD