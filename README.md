采用com4j来调用ocx组件


     java -Dfile.encoding=UTF-8 -jar tlbimp.jar -o 路径 -p 包名 组件路径



注意：先要注册组件，最好是将组件放入到system32或者64里

通过上面的代码会自动生成ocx组件里的方法与事件，结构如下：
     -tdm
         +--events
            ---+__CTISrv
         +--CTISrv__v2
         +--eeUerType
         +--ClassFactory


如何调用：
自动生成的代码中会有Class工厂类，获取对象后，调用advise，来加载事件对象集成的类

     mainForm = ClassFactory.createMainForm();
     this.cookie = mainForm.advise(__CTISrv.class, myIMainFormEvents);
