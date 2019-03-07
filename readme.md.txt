### Promise:解决异步回调地狱。
let p = new Promise((resolve,reject)=>{
      $.ajax({
          url:'data/1.txt',
          dataType:'json',
          success(res){
              // 成功
              resolve(res);
          },
          error(e){
              reject(e);
          }
      })
})

let p1 = $.ajax({url:'data/1.txt',dataType:'json'});
高版本 jquery中  $ajax() 返回 Promise对象

// 一个请求
p.then((res)=>{
    //成功代码
},(e)=>{
   // 失败代码
})
// 多个请求：
p.all([p1,p2]).then((result)=>{
    let [arr1,arr2] =result;
    console.log(arr1,arr2);
},(e)=>{
    // 失败
})

### axios 实现 ajax 

注意：
   Vue 中  vue-resource 实现传统 ajax
   Vue 中  axios 实现 Promise 的同步写法执行异步代码

                    // 用 axios 封装 ajax
                    this.$axios.get('data/1.txt')
                        .then((res) => {
                            //成功代码
                            //console.log(res);
                            this.res1 = res.data;
                        })
                        .catch((e) => {
                            // 失败代码
                            console.log(e);
                        })
