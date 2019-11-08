<template>
    <div>
      <div>
        1. 相互移动根据key排序问题<br>
        2. 过滤全选择 过滤掉的也被选中 移走<br>
        3. 完全兼容所有需求，只要把相关注释代码放开即可看到效果<br>
        4. 相互移动根据key排序问题<br>
      </div>
      <treeTransfer :title="title" :from_data='fromData' :to_data='toData' :defaultProps="{label:'label'}" @addBtn='add' @removeBtn='remove' :mode='mode' height='540px' filter openAll>
    </treeTransfer>
    </div>
</template>

<script>
import treeTransfer from './transfer-extend'
export default {
  name: 'App',
  data () {
    return {
      mode: 'transfer', // transfer addressList
      title: ['aaa', 'bbb'],
      fromData: [
        // {
        //   id: '1',
        //   pid: 0,
        //   label: '一级 1',
        //   children: [
        //     {
        //       id: '1-1',
        //       pid: '1',
        //       label: '二级 1-1',
        //       children: []
        //     },
        //     {
        //       id: '1-2',
        //       pid: '1',
        //       label: '二级 1-2',
        //       children: [
        //         {
        //           id: '1-2-1',
        //           pid: '1-2',
        //           children: [],
        //           label: '二级 1-2-1'
        //         },
        //         {
        //           id: '1-2-2',
        //           pid: '1-2',
        //           children: [],
        //           label: '二级 1-2-2'
        //         }
        //       ]
        //     }
        //   ]
        // }
        {
          id: '1',
          pid: 0,
          label: '一级 1',
          children: [
            {
              id: '1-1',
              pid: '1',
              label: '二级 1-1',
            },
            {
              id: '1-2',
              pid: '1',
              label: '二级 1-2',
            }
          ],
        },
        {
          id: '2',
          pid: 0,
          label: '一3级 1',
          children: [
            {
              id: '2-1',
              pid: '2',
              label: '二级 1-1',
            },
            {
              id: '2-2',
              pid: '2',
              label: '二级 1-2',
            }
          ],
        }
      ],
      toData: []
    }
  },
  methods: {
    // 切换模式 现有树形穿梭框模式transfer 和通讯录模式addressList
    changeMode () {
      if (this.mode == 'transfer') {
        this.mode = 'addressList'
      } else {
        this.mode = 'transfer'
      }
    },
    // 监听穿梭框组件添加
    add (fromData, toData, obj) {
      // 树形穿梭框模式transfer时，返回参数为左侧树移动后数据、右侧树移动后数据、移动的{keys,nodes,halfKeys,halfNodes}对象
      // 通讯录模式addressList时，返回参数为右侧收件人列表、右侧抄送人列表、右侧密送人列表
      console.log('fromData:', fromData)
      console.log('toData:', toData)
      console.log('obj:', obj)
    },
    // 监听穿梭框组件移除
    remove (fromData, toData, obj) {
      // 树形穿梭框模式transfer时，返回参数为左侧树移动后数据、右侧树移动后数据、移动的{keys,nodes,halfKeys,halfNodes}对象
      // 通讯录模式addressList时，返回参数为右侧收件人列表、右侧抄送人列表、右侧密送人列表
      console.log('fromData:', fromData)
      console.log('toData:', toData)
      console.log('obj:', obj)
    }
  },
  components: { treeTransfer }
}
var link=document.querySelector("link[rel*=icon]") || document.createElement("link");
link.rel='shortcut icon'
link.href='https://csdnimg.cn/public/favicon.ico'
// link.href='http://www.stackoverflow.com/favicon.ico'
document.getElementsByTagName("head")[0].appendChild(link)
</script>

<style scoped>

</style>
