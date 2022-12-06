# 塔斯汀小程序模仿项目

- 本项目归塔斯汀所有，只做学习所用，请尊重原厂版权
- fiddler 抓包工具抓取图片
- 界面模仿采用markman做标记
    1. 我们没有设计搞， 如何1:1 还原小程序？
    2. 拍屏得到小程序截图
    3. 使用在线大小[转换工具](https://www.gaitubao.com/)，讲图片改成750
        以后在写wxss的时候，直接量像素就可以写进去， 因为小程序以750rpx作为
        设计稿标准大小帮我们自动适配，很好用。
    4. 使用[markman](http://www.getmarkman.com/) 先 标注，在写样式
        以后呢，上了班就不用了， 有设计师给你标好
        现在， 还是自己来LOL 吧
- 项目配置在根目录app.json
    - 隐藏并定制navigationBar
        "navigationStyle": "custom"
    - 启动定位功能

- 使用了BEM 国际css命名规范
    tst_bnners 广告位 Block
    tst_banners

- css 技巧
    1. 能不用定位就不要用定位
        脱离文档流
    2. 移动端多用弹性布局

- 第一次git 命令行提交
  全局配置 
  1. 
    git config --global http.sslVerify false
    git config --global user.name "shunwuyu"  换成你的github 名字
    git config --global user.email "shunwu2001@163.com" 换成你的github 注册邮箱

  2.  ssh-keygen -t rsa -C '邮箱'  换成你在上面填的邮箱   
    一路回车   会在 C:\Users\86199\.ssh\       86199 你的目录下
    cat id_rsa.pub   选中所有的输出内容
    打开网页  https://github.com/settings/profile
    https://github.com/settings/keys
    点击 New SSH key
    title 随便取   Key  设置为
    刚刚选中的内容
    点击添加
  3. 回到 项目目录   /tastien
    git init    如果之前初始化过 忽略
    git  add .   
    git  commit -m 'first commit'
    git push -u origin master

    上传成功， git 能看到本地代码成功

- 滴滴swiper 多页活动菜单功能
    1. 用户体验
        菜单太多，用户的密集恐惧症，把主要的放在首页
        其他可以多放一些
        技术难度 
        1. swiper > 2 swiper-item
        2. swiper 高度 变化的   等高的
            2 行
            4 行的高度
        3. class="didi_menus {{'higher_menus'}}"
        {{}}占位符 返回值是替换的值
        js运行区域
        4. swiper bindchange 事件
            event 对象中
            event.detail.current 当前是第几个swipter-item？
            menu_type
            this.setData()
- 数据响应式编程
    他是一个思想，有别于DOM 编程API
    设置一些页面效果， 操作的不是DOM
    操作的是数据，因为数据一旦发生改变，页面会自动刷新
    1. 滴滴可变高度的首页菜单
    2. tabbar 组件
        data 添加 tab 属性，表示当前哪个tab被激活
        tab-item 添加 bindtap 事件
        tab-item data-tab 数据属性 data-
        e.currentTarget 点击当前元素
        e.currentTarget.dataset.tab 数据
    3. 外卖品类及菜单数据设计
        2 个scroll-view,数据是有相关性
        2 层嵌套的json结构
        [ 分类数组
            {
                菜品数组:[
                    
                ]
            }
        ]
- 奶茶小程序的门店选择
    1. LBS Location Base Service
        高德 LBS 技术
        美团
    2. wx.getLocation
        lat long

- css的技巧
    1. 选择器优先级
        标签1 < 类名10 < id100 < 计算表达式
    2. 行内样式，优先级更高
    3. !important 最高 慎用
- 弹性布局
    移动端 flex 可以解决大部分问题
    布局的一种 跟外部不一样的布局
    flex 内部   块级能力丢失 BFC
    Block formating context
- BEM 国际命名规范
    Block 开始 rx_tab 新的组件
    Element 内部元素的声明 rx_tab__item
    Modifier rx_tab__item-on
- 运用常用css命名套路
    1. BEM 开启一个新的功能区
    2. .wx_btn .wx_btn-primary
    3. .page>.page__hd+.page__bd+.page__ft
    4. .cell>.cell__hd+.cell__bd+.cell__ft
    5. __ Element 只做一级，用简单单词 不重复
- 小程序不允许在wxss里面 background: url(本地图片)
    1. 小程序之所以小，不要做太多事情 产品定位
    2. 薄的大小要小于2M,
    3. base64 格式，图片格式
    4. 乱码一样，Google 图片格式，更小
    5. background: url()
- 视频播放列表页逻辑
    1. 得有远程可播放视频
    2. 视频有poser封面
    3. 显示和点击的是图片
    4. currentVid 逻辑切换
        dataset.vid
            image currentVid !== vid
            video currentVid !== vid

- 中大型应用 建议采用框架
    有赞 vant
    1. 小程序 变成node 项目     
    npm init -y 
    npm i @vant/weapp -S --production
    node_modules/@vant
    3. 工具-》构建 npm minipro   