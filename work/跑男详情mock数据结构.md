```json
runDetailInfo:{
    // 1 自己 2 跑男 3 用户 4 其他参观者
    visitorType: Number,
    // 用户昵称
    userName: String,
    // 头衔
    userTitle: String,
    // 宣言
    declaration: String (15个字符以内),
    // 头像
    avatar: String,
    // 收藏数目
	collectionCount: number,
    //	点赞数目
    thumbUpCount: number,
    //	参观数目
    visitorCount: number,
    // 收入
    inCome: number,
    // 评论数目
    commentsCount: number,
    // 工作时间
    workingTime: Date,
    // 经验
    experience: number,
    // 邀请用户数目
    recommendUsers: number,
    // 服务用户数目
    serviceUsers: number,
    // 等级
    grade: nmber,
    // 相册  照片地址数组
    album: Array,
    //  二维码
    QRcode: Url
}
```

```json
commentList:{
  page: 1,
  "list|1-10": [
    {
      userName: Random.cname(),
      avatar: Random.image('200x100'),
      'thumbUpUser|1-10': [
        {
          thumbUpAvatar: "@image('200x100')",
        }
      ],
      commentContent: Random.cparagraph(2, 3),
      isThumbUp: false,
      commentDate: Random.date('yyyy-MM-dd'),
    },
  ]
} 
```

```json
visitorInfo:
{
    page:1,
    visitorList:[
        {
            userName: String,
            avatar: String,
            title:String,
            visitDate: new Date()
        }
    ]
}
```

```
collectionInfo:
{
    page:1,
    visitorList:[
        {
            userName: String,
            avatar: String,
            title:String,
            visitDate: new Date()
        }
    ]
}
```

```json
orderList:{
    page: 1
    [
    	{
            completeDate: Date,
            orderNumber: Num,
            orderIncome: Num
            takeTime: Date,
            commentsWord: String,
            distance: String
        }
    ]
}
```

