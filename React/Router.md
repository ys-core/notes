
<Link to={`/article/${this.props.content.key}?username=yongsongLee`}> 在to属性中插入动态值和传参
this.props.match.params.index***将获得this.props.content.key的值
this.props.location.search将获得参入的参数?username=yongsongLee


