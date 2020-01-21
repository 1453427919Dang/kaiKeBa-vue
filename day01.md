#v-if和v-for哪个优先级高？如果两个同时出现，应该怎么优化得到更好的性能？
  1、当v-if和v-for在同一节点使用时，v-for的优先级更高一些，v-if会重复运行于v-forv-for每个循环中
  2、优化方式：
     （1）、将v-if和v-for放在不同的标签里面，先使用v-if进行判断，再使用v-for进行循环处理。
     （2）、将需要遍历的数据放在计算属性中遍历之后再返回。
     如下：
     利用计算属性遍历数据：
     computed: {
        activeStudent: function () {
        return this.students.filter(function (student) {
        return student.isActive
        })
      }
    }
    使用：
    <ul>
        <li
            v-for="student in activeStudent"
            :key="student.id"
            >
            {{ student.name }}
        </li>
    </ul>




