<template>
    <div class="register">
      <div class="bookmar">ABC图书馆管理系统</div>
    <div class="img">
      <img src="../assets/开心工作.svg" alt />
    </div>
        <section class="form_container">
            <el-form :model="register" :rules="rules" class="registerForm" ref="registerForm" label-width="100px"  >
                <el-form-item label="账号" prop="account">
                    <el-input v-model="register.account" placeholder="请输入账号" ></el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input v-model="register.password" placeholder="请输入密码" type="password"></el-input>
                </el-form-item>
                <el-form-item label="确认密码" prop="password2">
                    <el-input v-model="register.password2" placeholder="请确认密码" type="password"></el-input>
                </el-form-item>
                <el-form-item label="姓名" prop="name">
                    <el-input v-model="register.name" placeholder="请输入用户名"></el-input>
                </el-form-item>
                <el-form-item label="邮箱" prop="email">
                    <el-input v-model="register.email" placeholder="请输入邮箱"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary"  class="submit_btn" @click="submitForm('registerForm')">注 册</el-button>
                </el-form-item>
            </el-form>
        </section>
    </div>
</template>

<script>
export default {
  name: "register",
 //    判断密码是否一致；
  data() {
    var validatePass2 = (rule, value, callback) => {
      if (value !== this.register.password) {
        callback(new Error("两次输入密码不一致!"));
      } else {
        callback();
      }
    };
    return {
       register: {
        accont: "",
        name: "",
        email: "",
        password: "",
        password2:""
      },
//    在return 后面；
      rules: {
      // 要以数组形式展示
        account:[
           { required: true, message: "ID不能为空", trigger: "blur" },
           { min: 8, max: 30, message: "长度在 8 到 30 个字符", trigger: "blur" },
           {
        trigger: 'blur',
        validator: (rule, value, callback) => {
          var account = /^[0-9]*$/
          if (!account.test(value)) {
            callback(new Error('密码必须由大小写字母、特殊字符组合,请输入8-30位'))
          }else{
            callback()
          } 
        }
           }
        ],
        name: [
          { required: true, message: "用户名不能为空", trigger: "blur" },
          { min: 2, max: 40, message: "长度在 2 到 30 个汉字", trigger: "blur" }
        ],
        email: [
          {
            type: "email",
            required: true,
            message: "邮箱格式不正确",
            trigger: "blur"
          }
        ],
        password: [
          { required: true, message: "密码不能为空", trigger: "click" },
          { min: 8, max: 30, message: "长度在 8到 30 个字符", trigger: "blur" },

         {
        trigger: 'blur',
        validator: (rule, value, callback) => {
          var passwordreg = /(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*?])/
          if (!passwordreg.test(value)) {
            callback(new Error('密码必须由大小写字母、特殊字符组合,请输入8-30位'))
          }else{
            callback()
          }
        } 
        }
        ],
        password2: [
          { required: true, message: "确认密码不能为空", trigger: "blur" },
          {
            min: 8,
            max: 30,
            message: "长度在 8 到 30 个字符",
            trigger: "blur"
          },
          { validator: validatePass2, message: "密码必须一致",trigger: "blur" }
        ]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
      this.$axios({
        method:"post",
        url:"/regist",
        data:this.register
      }).then((res)=>{
        console.log(res);
        console.log("传入的数据="+JSON.stringify(this.register));
        if(res.data===1)
        {
          alert("注册成功")
        }
        else if(res.data===0){
          alert("账号已经存在")
        }
        

      })
      .catch(function(error){
        console.log(error);
      });
        } else {
          console.log("error submit!!");
          alert("提交失败");
          return false;
        }
      });
    }
  }
};
</script>

<style>
.register{
    display: flex;
  justify-content: space-around;
 
}
.form_container .el-form {
  width: 20em;
  border: 2px;
  flex: 2;
  margin-right:18em; 
  margin-top:15% 


}

.img {
  height: 40%;
  width: 40%;
  display: inline-block;
  flex: 3;
  margin-right:20%; 
}
.bookmar {
  font-family: "FZQuSJW";
  font-size: 1em;
  text-align: left;
  height: 30px;
    flex: 1;
}
</style>