# 2026央视春晚魔术《惊喜定格》——魔术计算器技术实现文档
网站试用：https://www.springfestival.yeefish.qzz.io/
## 一、项目说明
本项目为个人开源作品，是对 2026 年央视春晚魔术节目《惊喜定格》的**技术原理还原与前端实现**。

- 代码完全独立编写
- 仅用于学习、交流、娱乐
- 非官方程序，与中央广播电视总台无任何关联
- 不使用任何春晚官方音视频、图片素材

---


## 二、魔术原理

### 核心机制
- **时间编码**：魔术计算器会将当前系统时间（月+日+时+分）编码为一个7-8位的目标数字。
- **双阶段输入**：
  1. 观众输入一个4位数
  2. 观众输入一个5位数
  3. 按下“+”号后，计算器进入“魔术盲按模式”
- **盲按效果**：此时无论观众按任何数字键，屏幕都会显示“目标数字 - 第一个4位数”的差值，营造出计算器“预知未来”的错觉。
- **最终揭晓**：当按下“=”号时，屏幕会直接显示预先编码的目标数字，完成“惊喜定格”。

### 目标数字生成规则
```javascript
function getMagicNumber(){
  let d = new Date();
  let m = d.getMonth() + 1;
  let day = d.getDate().toString().padStart(2,'0');
  let h = d.getHours().toString().padStart(2,'0');
  let min = d.getMinutes().toString().padStart(2,'0');
  return parseInt(m + day + h + min);
}
