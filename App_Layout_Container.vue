<template>
  <div id="App_Layout_Container">
    <el-row type="flex" justify="center">
      <h2 class='header-h2'>22B L3 CI REPORT</h2>
    </el-row>

    <el-row :gutter="0" type="flex" justify="center">
      <el-col :span="3">
        <div>
          <span> 用例度量</span>
        </div>
      </el-col>
      <el-col :span="3">
        <div>
          <span> 代码检查</span>
        </div>
      </el-col>
      <el-col :span="3">
        <div>
          <span> 软件成本</span>
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="20" class="row-header" type="flex" justify="center">
      <el-col :span="3">
        <div>
          <a href="http://3ms.huawei.com/hi/group/2691547/wiki_4939973.html">L3工程能力全景图</a>
        </div>
      </el-col>
      <el-col :span="3">
        <div>
          <a href="http://3ms.huawei.com/hi/group/2691547/wiki_6166014.html">L3工程能力需求收集</a>
        </div>
      </el-col>
      <el-col :span="3">
        <div>
          <a href="https://5g.rnd.huawei.com/list_markinfo/">CI邮件订阅退订链接</a>
        </div>
      </el-col>
      <el-col :span="3">
        <div>
          <a href="https://5g.rnd.huawei.com/ci/query/22B/">CID滚动报告链接</a>
        </div>
      </el-col>
    </el-row>

    <el-row :gutter="20">
      <!-- gutter 栅格间距 -->
      <el-col>
        <el-container style="height: 500px; border: 1px solid #eee">
          <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
            <el-menu :default-openeds="['1', '5']">
              <el-submenu index="1">
                <template slot="title"><i class="el-icon-message"></i>领域 L3</template>
                <el-menu-item-group>
                  <el-submenu index="1-1">
                    <template slot="title">CU用户</template>
                    <el-submenu index="1-1-1">
                      <template slot="title">NSA管理</template>
                    </el-submenu>
                    <el-submenu index="1-1-2">
                      <template slot="title">基础性能</template>
                    </el-submenu>
                    <el-submenu index="1-1-3">
                      <template slot="title">承载算法</template>
                    </el-submenu>
                    <el-submenu index="1-1-4">
                      <template slot="title">承载管理</template>
                    </el-submenu>
                    <el-submenu index="1-1-5">
                      <template slot="title">接口管理</template>
                    </el-submenu>
                    <el-submenu index="1-1-6">
                      <template slot="title">移动流程</template>
                    </el-submenu>
                    <el-submenu index="1-1-7">
                      <template slot="title">移动算法</template>
                    </el-submenu>
                  </el-submenu>
                  <el-submenu index="1-2">
                    <template slot="title">DU小区</template>
                    <el-menu-item index="1-4-1">选项4-1</el-menu-item>
                  </el-submenu>
                  <el-submenu index="1-3">
                    <template slot="title">DU用户</template>
                    <el-menu-item index="1-4-1">选项4-1</el-menu-item>
                  </el-submenu>
                  <el-submenu index="1-4">
                    <template slot="title">L2高频</template>
                    <el-menu-item index="1-4-1">选项4-1</el-menu-item>
                  </el-submenu>
                  <el-submenu index="1-5">
                    <template slot="title">基站技术开发部</template>
                    <el-menu-item index="1-4-1">选项4-1</el-menu-item>
                  </el-submenu>
                </el-menu-item-group>
              </el-submenu>
            </el-menu>
          </el-aside>

          <!-- 右边边栏 -->
          <!-- 右边边栏 -->
          <el-container>
            <!-- 头顶容器 -->
            <el-table
                :data="tableData"
                style="width: 100%"
                row-key="id"
                border
                default-expand-all
                :tree-props="{children: 'children', hasChildren: 'hasChildren'}">
              <el-table-column
                  prop="domain"
                  label="领域"
                  width="200">
              </el-table-column>
              <el-table-column label="原生覆盖率数据（对外发布的覆盖率数据)">
                <el-table-column
                    prop="LF"
                    label="LF"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="FNF"
                    label="FNF"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="BRF"
                    label="BRF"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="row"
                    label="行覆盖率"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="fx"
                    label="函数覆盖率"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="branch"
                    label="分支覆盖率"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="report"
                    label="覆盖报告"
                    width="120">
                </el-table-column>
              </el-table-column>
              <el-table-column label="脱水版覆盖率数据">
                <el-table-column
                    prop="water_row"
                    label="脱水版行覆盖率"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="water_cov"
                    label="脱水版覆盖报告"
                    width="120">
                </el-table-column>
              </el-table-column>
              <el-table-column label="非正常覆盖数据">
                <el-table-column
                    prop="risk"
                    label="高危代码未覆盖"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="nofx"
                    label="函数未覆盖"
                    width="120">
                </el-table-column>
                <el-table-column
                    prop="branch_cov"
                    label="分支覆盖<50%"
                    width="120">
                </el-table-column>
              </el-table-column>
            </el-table>
          </el-container>


        </el-container>

        <!-- </div> -->
      </el-col>
    </el-row>
  </div>
</template>

<script>


export default {
  name: 'App_Layout_Container',
  data() {
    return {
      tableData: [{
        id: 1,
        domain: 'L3',
        LF: '1370177',
        FNF: '304685',
        BRF: '1317444',
        row: '84.21%',
        fx: '87.90%',
        branch: '57.68%',
        report: '--',
        water_row: '90.11%',
        water_cov: '--',
        risk: '2541',
        nofx: '5978',
        branch_cov: '2194',
        children: [{
          id: 11,
          domain: 'depart:CU用户',
          LF: '1370177',
          FNF: '304685',
          BRF: '1317444',
          row: '84.21%',
          fx: '87.90%',
          branch: '57.68%',
          report: '--',
          water_row: '90.11%',
          water_cov: '--',
          risk: '2541',
          nofx: '5978',
          branch_cov: '2194',
          children: [{
            id: 111,
            domain: 'domain:NSA管理',
            LF: '1370177',
            FNF: '304685',
            BRF: '1317444',
            row: '84.21%',
            fx: '87.90%',
            branch: '57.68%',
            report: '--',
            water_row: '90.11%',
            water_cov: '--',
            risk: '2541',
            nofx: '5978',
            branch_cov: '2194',
            children: [{
              id: 111,
              domain: 'subdomain:NSA管理/n' +'/n'+
                  'PL:马盛菁m00439621',
              LF: '1370177',
              FNF: '304685',
              BRF: '1317444',
              row: '84.21%',
              fx: '87.90%',
              branch: '57.68%',
              report: '--',
              water_row: '90.11%',
              water_cov: '--',
              risk: '2541',
              nofx: '5978',
              branch_cov: '2194',
            }, {
              id: 112,
              domain: 'subdomain:NSA管理_OCL' +
                  'PL:马盛菁m00439621',
              LF: '1370177',
              FNF: '304685',
              BRF: '1317444',
              row: '84.21%',
              fx: '87.90%',
              branch: '57.68%',
              report: '--',
              water_row: '90.11%',
              water_cov: '--',
              risk: '2541',
              nofx: '5978',
              branch_cov: '2194',
            }]
          }, {
            id: 112,
            domain: 'domain:基础性能',
            LF: '1370177',
            FNF: '304685',
            BRF: '1317444',
            row: '84.21%',
            fx: '87.90%',
            branch: '57.68%',
            report: '--',
            water_row: '90.11%',
            water_cov: '--',
            risk: '2541',
            nofx: '5978',
            branch_cov: '2194',
          }]
        }, {
          id: 12,
          domain: 'depart:DU小区',
          LF: '1370177',
          FNF: '304685',
          BRF: '1317444',
          row: '84.21%',
          fx: '87.90%',
          branch: '57.68%',
          report: '--',
          water_row: '90.11%',
          water_cov: '--',
          risk: '2541',
          nofx: '5978',
          branch_cov: '2194',
        }]
      }, {
        id: 2,
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        id: 3,
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄',
        children: [{
          id: 31,
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          id: 32,
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }]
      }, {
        id: 4,
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }],
    }
  },
};
</script>


<style>
.el-row {
  margin-bottom: 20px;
}

.el-col {
  border-radius: 4px;
}

.bg-purple {
  background: #d3dce6;
}

.grid-content {
  border-radius: 4px;
  min-height: 36px;
}

</style>