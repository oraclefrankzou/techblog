   
    ExtJs消息弹出提示框
    
    实现消息提示框弹出功能，显示时间可以自定义， 我们把弹出框可以根据需要放到不同的位置.
    
    参数: color,主窗口显示颜色; msg,定义显示的消息内容。

    
    //消息弹出框
displayWin=function(color,msg) {
    //如果消息弹出框不存在，那么就要新建一个
    if (!Ext.getCmp("promptWin")){
        {
            var promptWin = new Ext.Window({
                title: "",
                id: "promptWin",
                layout: "fit",
                width: 200,
                height: 50,
                x: document.body.clientWidth / 2,
                y: 4,
                border: false,
                bodyBorder:false,
                closable: true,
                header: false,
                draggable:false,
                resizable:false,
                items: [
                    {html: "", id: "prompttext", style: "margin-top:15px;margin-left:5px"}
                ]
            });
        }
    } else{
        var promptWin=promptwin=Ext.getCmp("promptWin");
    }

    //显示消息框
    promptWin.setBodyStyle("background-color", color);
    promptWin.show();
    Ext.get("prompttext").dom.innerHTML = "温馨提示:" + msg + ".(" + displaySeconds + "秒)";
}
//信息弹出框ends


//定时器任务,更新消息框计时和关闭框
var task={
     run:function(){
         var timeInterval=Ext.get("prompttext").dom.innerHTML;
         if (parseInt(timeInterval.substr(-3,1))>0){
             Ext.get("prompttext").dom.innerHTML=timeInterval.substr(0,timeInterval.length-3)+(timeInterval.substr(-3,1)-1)+"秒)";
         };
         if (parseInt(timeInterval.substr(-3,1))==0)
         {
             Ext.get("prompttext").dom.innerHTML='';
             var promptwin=Ext.getCmp("promptWin");
             promptwin.close();
         }
     },

     interval:1000
};
Ext.TaskManager.start(task);
 //消息弹出窗口ends

 });
 
 效果:
 
 
 ![image](https://github.com/oraclefrankzou/techblog/blob/master/images/promptwin.png)
 
 
 
 
 
