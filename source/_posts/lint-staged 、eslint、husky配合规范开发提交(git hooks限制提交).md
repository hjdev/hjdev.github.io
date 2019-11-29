#### Eslint配置

如何配置不详讲了，网上很多教程，.eslintrc.js是我常用到的规范

```json
module.exports = {
  root: true,
  parserOptions: {
    parser: "babel-eslint"
  },
  env: {
    browser: true,
  },
  extends: [
    // https://github.com/vuejs/eslint-plugin-vue#priority-a-essential-error-prevention
    // consider switching to `plugin:vue/strongly-recommended` or`plugin:vue/recommended`     //for stricter rules.
    "plugin:vue/essential",
    // https://github.com/standard/standard/blob/master/docs/RULES-en.md
    "standard"
  ],
  // required to lint *.vue files
  plugins: [
    "vue"
  ],
  // add your custom rules here
  rules: {
    /**
     \* 错误等级：off(0) | warn(1) | error(2)
     \* 处理方式：never | always
    */
    // 强制 generator 函数中 * 号周围使用一致的空格
    "generator-star-spacing": "off",
    // 强制使用一致的缩进
    "indent": [1, 4, {
      "SwitchCase": 1
    }],
    // 强制在 函数 的左括号之前使用一致的空格
    "space-before-function-paren": [0, "always"],
    // 操作符周围有空格
    "space-infix-ops": [2, { "int32Hint": false }],
    // 禁止使用多个空格
    "no-multi-spaces": [0],
    // 禁止出现未使用过的变量
    "no-unused-vars": [0],
    // 禁止出现多行空行
    "no-multiple-empty-lines": [0],
    // return 语句中不能有赋值表达式
    "no-return-assign": [0],
    // 禁止无用的表达式
    "no-unused-expressions": [0],
    // 立即执行函数表达式的小括号风格
    "wrap-iife": [0, "inside"],
    // 禁用 debugger 调试器：生成环境禁止使用
    "no-debugger": process.env.NODE_ENV === "production" ? "error" : "off"
  }
}
```

#### lint-staged 、husky配置

1、首先，我们使用下面的命令把 husky 和 lint-staged 安装到 Node.js 项目的 `devDependencies` 中：

```node
npm install husky lint-staged --save-dev
```

2、修改 package.json 配置

将下面的代码加入 package.json文件中：

```json
{
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.{vue, js}": [
    	"eslint --fix --quiet",
    	"git add"
    ]
  }
}
```

这样，当在终端输入 `git commit` 命令提交代码的时候，Lint 程序便会自动检查本次提交所修改的文件是否符合本项目的代码规范。如果代码不符合规范，便会拒绝提交代码。

![使用 husky 后提交](https://user-gold-cdn.xitu.io/2018/12/6/16782fd07b97cd70?imageView2/0/w/1280/h/960/format/webp/ignore-error/1)

如果想要跳过 Lint 程序，可以使用 `git commit -no-verify` 进行提交。