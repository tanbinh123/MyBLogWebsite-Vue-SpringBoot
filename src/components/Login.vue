<template>
<!--登陆弹框-->
<el-dialog title="登陆弹框" :visible.sync="visible">
    <el-form>
        <el-form-item label="用户名">
            <el-input v-model="login_id" autocomplete="off"></el-input>
        </el-form-item>
        <el-form-item label="密码">
            <el-input placeholder="请输入密码" v-model="login_pwd" show-password></el-input>
        </el-form-item>
    </el-form>
    <a class="column" style="margin-right:10px;" href='https://github.com/login/oauth/authorize?client_id=b9a7e7c8b699fa169b33&state=STATE&redirect_uri=http://localhost:8083/api/user/RegisterByGithub' target="_blank">
        <svg t="1622195461481" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2347" width="32" height="32">
            <path d="M1021.72444445 512a495.16088889 495.16088889 0 0 1-97.57582223 299.64515555 500.62222222 500.62222222 0 0 1-250.85724444 184.22897778 30.58346667 30.58346667 0 0 1-26.2144-4.73315555 25.85031111 25.85031111 0 0 1-8.00995556-20.02488889v-139.81013334a119.05706667 119.05706667 0 0 0-34.58844444-94.29902222 473.31555555 473.31555555 0 0 0 67.72053333-11.65084444 248.30862222 248.30862222 0 0 0 62.2592-26.2144 187.50577778 187.50577778 0 0 0 53.52106667-43.69066667 209.35111111 209.35111111 0 0 0 36.40888889-69.90506667 334.2336 334.2336 0 0 0 13.83537778-100.12444444 191.87484445 191.87484445 0 0 0-52.7928889-136.53333333 176.21902222 176.21902222 0 0 0-5.09724444-135.44106667 87.01724445 87.01724445 0 0 0-53.52106666 7.28177778 341.87946667 341.87946667 0 0 0-61.16693334 29.12711111l-25.12213333 15.65582222a473.31555555 473.31555555 0 0 0-254.86222223 0c-7.28177778-5.09724445-16.384-10.55857778-28.03484444-17.84035555A371.00657778 371.00657778 0 0 0 300.82844445 220.72888889a94.29902222 94.29902222 0 0 0-57.16195556-9.10222222 178.40355555 178.40355555 0 0 0-4.73315556 136.53333333 197.70026667 197.70026667 0 0 0-52.4288 137.26151111A327.68 327.68 0 0 0 200.33991111 584.81777778a223.55057778 223.55057778 0 0 0 36.40888889 69.90506667 172.94222222 172.94222222 0 0 0 53.52106667 44.41884444 304.7424 304.7424 0 0 0 62.2592 26.2144 471.13102222 471.13102222 0 0 0 68.08462222 11.65084444 105.22168889 105.22168889 0 0 0-32.768 68.44871112 112.86755555 112.86755555 0 0 1-30.21937778 9.4663111 190.41848889 190.41848889 0 0 1-36.40888889 3.2768A78.6432 78.6432 0 0 1 274.61404445 803.27111111a124.5184 124.5184 0 0 1-36.4088889-41.50613333 109.22666667 109.22666667 0 0 0-32.03982222-34.58844445 91.7504 91.7504 0 0 0-32.768-16.01991111h-13.1072a47.33155555 47.33155555 0 0 0-19.29671111 2.91271111q-5.46133333 3.2768-3.2768 7.64586667a50.24426667 50.24426667 0 0 0 6.18951111 9.10222222 62.98737778 62.98737778 0 0 0 8.73813334 8.37404445l4.73315555 2.91271111a88.83768889 88.83768889 0 0 1 29.12711111 25.12213333 179.49582222 179.49582222 0 0 1 20.75306667 33.49617778l6.5536 15.29173333a82.28408889 82.28408889 0 0 0 29.12711111 41.14204445 109.22666667 109.22666667 0 0 0 44.05475556 18.93262222 223.18648889 223.18648889 0 0 0 45.8752 4.73315556 207.16657778 207.16657778 0 0 0 36.40888888-2.54862223l15.29173334-2.54862222v95.39128889a26.2144 26.2144 0 0 1-8.73813334 20.02488889 31.67573333 31.67573333 0 0 1-26.57848888 4.73315555 498.43768889 498.43768889 0 0 1-249.40088889-185.32124444A486.78684445 486.78684445 0 0 1 2.27555555 512a497.70951111 497.70951111 0 0 1 68.44871112-254.86222222A504.6272 504.6272 0 0 1 257.13777778 70.72426667 497.70951111 497.70951111 0 0 1 512 2.27555555a497.70951111 497.70951111 0 0 1 254.86222222 68.44871112A504.6272 504.6272 0 0 1 953.27573333 257.13777778 496.98133333 496.98133333 0 0 1 1021.72444445 512z" p-id="2348"></path>
        </svg>
        <span class="icon-words">github登录</span>
    </a>
    <div slot="footer" class="dialog-footer">
        <el-button @click="visible = false">取 消</el-button>
        <el-button type="primary" @click="login(login_id,login_pwd)">确 定</el-button>
    </div>
</el-dialog>
</template>

<script>
import axios from "axios";
import {
    Input,
    Form,
    FormItem,
    Button,
    Dialog
} from "element-ui"
export default {
    name: "Login",
    components: {
        "el-input": Input,
        "el-form": Form,
        "el-form-item": FormItem,
        "el-button": Button,
        "el-dialog": Dialog
    },
    props: {
        loginVisible: {
            type: Boolean,
            default: false
        }
    },
    data() {
        return {
            login_stat: false,
            login_id: '',
            login_pwd: '',
            visible: false
        };
    },
    watch: {
        loginVisible(newValue, oldValue) {
            this.visible = this.loginVisible
        }
    },
    methods: {
        
        login: function (id, pwd) {
            if (sessionStorage.login_stat) {
                alert("已经登录");
                location.replace("/admin_back");
            }
            axios
                .get("/api/user/login", {
                    params: {
                        user_id: id,
                        user_pwd: pwd,
                    },
                })
                .then((res) => {
                    if (res.data) {
                        console.log(res.data)
                        alert("登录成功");
                        sessionStorage.login_stat = res.data.data;
                        location.replace("/admin_back");
                    } else alert("登录失败");
                })
                .catch(function (error) {
                    alert("登录出错");
                    console.log(error);
                });
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
/*@import "bootstrap";*/
.login-dialog {
    position: fixed;
    top: 50%;
    left: 50%;
    display: inline-block;
    width: 200px;
    padding-bottom: 10px;
    vertical-align: middle;
    background-color: #fff;
    border-radius: 4px;
    border: 1px solid #ebeef5;
    font-size: 18px;
    box-shadow: 0 2px 12px 0 rgb(0 0 0 / 10%);
    text-align: left;
    overflow: hidden;
    backface-visibility: hidden;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
</style>
