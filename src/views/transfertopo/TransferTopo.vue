<template>
    <div class="c-main">
        <div id="topo">
        </div>
        <el-tabs v-model="activeName" @tab-click="handleClick">
            <el-tab-pane label="配置更新" name="first">
                <table class="c-table c-stripe c-border c-hover c-state">
                    <thead class="bg-thead">
                        <tr>
                            <th>数据更新时间</th>
                            <th>更新类型</th>
                            <th>资源类型</th>
                            <th>名称</th>
                            <th>类型</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="item in mockUsers" :key="item.id">
                            <td v-text="item.updatetime"></td>
                            <td v-text="item.updatetype"></td>
                            <td v-text="item.sourcetype"></td>
                            <td v-text="item.name"></td>
                            <td v-text="item.type"></td>
                        </tr>
                    </tbody>
                </table>
            </el-tab-pane>
            <el-tab-pane label="性能异常" name="second">性能异常</el-tab-pane>
            <el-tab-pane label="资源预警" name="third">资源预警</el-tab-pane>
        </el-tabs>
    </div>
</template>
<style lang="less" rel="stylesheet/less" scoped>

</style>
<script>
    let Mock = require('mockjs'); // 测试数据
    export default {
        name: 'TransferTopo',
        data () {
            return {
                activeName: 'first',
                box : new twaver.ElementBox(),
                network : new twaver.vector.Network(),
            }
        },
        computed: {
            mockUsers () {
                let data = {
                    'list|3-5': [
                        {
                            'id': '@guid',
                            'updatetime': '@datetime()',
                            'updatetype': '@pick(["增加", "减少"])',
                            'sourcetype': '@pick(["设备", "连纤"])',
                            'name': '@cword(5)',
                            'type': '@pick(["2.5G", "OSN 3500", "OSN 2500"])'
                        }
                    ]
                };
                let result = Mock.mock(data);
                return result.list;
            }
        },
        methods: {
            handleClick(tab, event) {
                console.log(tab, event);
            }
        },
        mounted(){
            console.log(twaver);
            let node = new twaver.Node();
            let box = new twaver.ElementBox();
            let network = new twaver.vector.Network(box);

            document.getElementById("topo").append(network.getView());
            network.adjustBounds({x:0,y:0,width:document.documentElement.clientWidth - 340,height:500});
            let node1 = new twaver.Node({
                name:'传输系统1',
                location:{x:100,y:100},
                width:50,
                height:50
            });
            box.add(node1);
            let node2 = new twaver.Node({
                name:'传输系统2',
                location:{x:400,y:100},
                width:50,
                height:50
            });
            box.add(node2);
            let node3 = new twaver.Node({
                name:'传输系统3',
                location:{x:700,y:100},
                width:50,
                height:50
            });
            box.add(node3);
            let node4 = new twaver.Node({
                name:'传输系统4',
                location:{x:100,y:300},
                width:50,
                height:50
            });
            box.add(node4);
            let node5 = new twaver.Node({
                name:'传输系统5',
                location:{x:400,y:300},
                width:50,
                height:50
            });
            box.add(node5);
            let node6 = new twaver.Node({
                name:'传输系统6',
                location:{x:700,y:300},
                width:50,
                height:50
            });
            box.add(node6);

            let link1 = new twaver.Link(node1,node2);
            // link1.setName('link1');
            link1.setStyle('link.color','#309FC9');
            link1.setStyle('select.color','orange');
            link1.setStyle('backward',true);
            link1.setStyle('link.width',1);
            box.add(link1);
            let link2 = new twaver.Link(node2,node5);
            // link2.setName('link2');
            link2.setStyle('link.color','#309FC9');
            link2.setStyle('select.color','orange');
            link2.setStyle('backward',true);
            link2.setStyle('link.width',1);
            box.add(link2);
            let link3 = new twaver.Link(node4,node5);
            // link3.setName('link3');
            link3.setStyle('link.color','#309FC9');
            link3.setStyle('select.color','orange');
            link3.setStyle('backward',true);
            link3.setStyle('link.width',1);
            box.add(link3);
            let link4 = new twaver.Link(node5,node6);
            // link4.setName('link4');
            link4.setStyle('link.color','#309FC9');
            link4.setStyle('select.color','orange');
            link4.setStyle('backward',true);
            link4.setStyle('link.width',1);
            box.add(link4);
            let link5 = new twaver.Link(node3,node6);
            // link5.setName('link5');
            link5.setStyle('link.color','#309FC9');
            link5.setStyle('select.color','orange');
            link5.setStyle('backward',true);
            link5.setStyle('link.width',1);
            box.add(link5);
        },
    }
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
    @import "./transferTopo.less";
</style>
