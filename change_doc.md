### 运行开发环境即可查看demo
#### 接口类修改
1. tabs 组件可以自定义下划线的宽度 [demo](http://localhost:8080/#/zh-CN/component/tabs)

    Tabs Attributes

    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    active-bar-width | 激活条(下划线)的宽度 | number | -- | --

2. tabs 组件可以提示小红点  [demo](http://localhost:8080/#/zh-CN/component/tabs)

    Tab-pane Attributes

    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    has-notice | 是否显示提示（小红点） | boolean | -- | false

3. table checkbox 自动隐藏 [demo](http://localhost:8080/#/zh-CN/component/table)

    Table Attributes

    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    auto-checkbox | 多选模式下，设置为 true，正常显示 index，鼠标移到 index 上或有选中项， CheckBox 才展示出来  | boolean | -- | false


4. select 组件异步加载数据 loading 态 [demo](http://localhost:8080/#/zh-CN/component/select)

    Tab-pane Attributes

    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    loading-icon | 输入框右边显示一个转圈 | boolean | -- | false

5. InputNumber 组件支持小数位数限制[demo](http://localhost:8080/#/zh-CN/component/input-number)

    InpuNumber Attributes

    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    decimal | 小数位数限制 | number | — | null 

6. popover 组件新增 mask 蒙版

    Popover Attributes
    
    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    mask | 是否显示蒙版 | boolean | — | false

7. popover 组件新增 didShow 回调、didHide 回调
   
   Popover Slot Methods
   
   传入popover 的 slot 组件，如果实现了 didShow、didHide 方法
   在popover show 和 hide 时会触发

8. cascader 支持传入 formatMethod 属性，接受一个方法
   用于自定义显示值

9. popover 新增 closeOnMask 属性
   设置了 mask 属性，并设置 closeOnMask 属性，点击蒙版触发关闭事件

10. switch 新增 loading 态
    
    Popover Attributes
    
    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    loading | 是否显示加载态 | boolean | — | false

11. menu 新增 notActivatedWhileClick 属性
    
    Popover Attributes
    
    参数 | 说明 | 类型 | 可选值 | 默认值
    ----|----|----|----|----
    notActivatedWhileClick | 点击menu-item的时候，不要高亮该menu-item | boolean | — | false


12. tab 新增了 custom slot，可以在tab栏最右侧插入自定义的按钮/输入框
    [demo](http://localhost:8088/#/zh-CN/component/tabs#ji-chu-yong-fa)

#### 优化类修改：
1. DatePicker 清除按钮 mouseenter 位置改变
2. DatePicker 选择时间范围，返回的 max date 为一天结束前一秒的时间
