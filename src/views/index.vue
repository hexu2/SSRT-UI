<template>
  <div class="app-container home">
    <el-row :gutter="20">
      <el-col :sm="24" :lg="24">
        <hr />
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :sm="24" :lg="12" style="padding-left: 20px">
        <h2>{{home_content.project_name}}</h2>
        <p>
         {{home_content.project_desc}}
        </p>
        <p>
          <b>current version:</b> <span>v{{ home_content.project_version }}</span>
        </p>
        <p>
          <el-button
            type="primary"
            size="mini"
            icon="el-icon-cloudy"
            plain
            @click="goTarget('https://github.com/hexu2/SSRT-Cloud.git')"
            >Github Source Codes</el-button
          >
        </p>
      </el-col>
    </el-row>
    <el-divider />
    <el-row :gutter="20">
      <el-col :xs="24" :sm="24" :md="12" :lg="8">
        <el-card class="update-log">
          <div slot="header" class="clearfix">
            <span>{{home_content.project_contacts_title}}</span>
          </div>
          <div class="body">
            <p>
              <i class="el-icon-user-solid">{{home_content.project_contacts_team.users}}</i>
            </p>
            <p>
              <i class="el-icon-phone">{{home_content.project_contacts_team.phone}}</i>
            </p>
          </div>
        </el-card>
      </el-col>
      <el-col :xs="24" :sm="24" :md="12" :lg="8">
        <el-card class="update-log">
          <div slot="header" class="clearfix">
            <span class="text-danger">{{home_content.maintenance_title}}</span>
          </div>
            <span v-for= "mitem in home_content.maintenance_content.reverse()" :key="mitem.index">
              <el-collapse accordion>
                <el-collapse-item v-bind:title="mitem.m_title" >
                  <ol>
                    <li v-for="m_details in mitem.m_details" :key="m_details.index">{{m_details.desc}}</li>
                  </ol>
                </el-collapse-item>
              </el-collapse>
            </span>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "Index",
  data() {
    return {
      // 版本号
      version: "1.0.0",
      home_content: {
        project_name: 'Self-Services Report Tool',
        project_desc: 'Help users to customize queries and generate reports.',
        project_version: '1.0.0',
        project_contacts_title: 'Contacts',
        project_contacts_team: {
          users: 'Blue Sky: Sam, Wangwei, hexu',
          phone: '+86 21 289xxxx335'
        },
        maintenance_title: 'System Maintenance Notice!!!',
        maintenance_content: [
          {
            m_title: 'v1.0.0 - 2022-03-19',
            m_details: [
              {
                id: '1',
                desc: 'Self-Services Report Tool - framework setup'
              }
            ]
          },
          {
            m_title: 'v1.0.0 - 2022-03-20',
            m_details: [
              {
                id: '1',
                desc: 'Self-Services Report Tool - update content to json'
              },
              {
                id: '1',
                desc: 'Self-Services Report Tool - testing'
              },
            ]
          }
        ]
      }
    };
  },
  methods: {
    goTarget(href) {
      window.open(href, "_blank");
    },
  },
};
</script>

<style scoped lang="scss">
.home {
  blockquote {
    padding: 10px 20px;
    margin: 0 0 20px;
    font-size: 17.5px;
    border-left: 5px solid #eee;
  }
  hr {
    margin-top: 20px;
    margin-bottom: 20px;
    border: 0;
    border-top: 1px solid #eee;
  }
  .col-item {
    margin-bottom: 20px;
  }

  ul {
    padding: 0;
    margin: 0;
  }

  font-family: "open sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  color: #676a6c;
  overflow-x: hidden;

  ul {
    list-style-type: none;
  }

  h4 {
    margin-top: 0px;
  }

  h2 {
    margin-top: 10px;
    font-size: 26px;
    font-weight: 100;
  }

  p {
    margin-top: 10px;

    b {
      font-weight: 700;
    }
  }

  .update-log {
    ol {
      display: block;
      list-style-type: decimal;
      margin-block-start: 1em;
      margin-block-end: 1em;
      margin-inline-start: 0;
      margin-inline-end: 0;
      padding-inline-start: 40px;
    }
  }
}
</style>

