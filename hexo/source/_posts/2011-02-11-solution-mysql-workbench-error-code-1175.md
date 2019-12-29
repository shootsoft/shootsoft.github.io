---
id: 110
title: 'MySQL Workbench “Error Code: 1175” 的解决方法'
date: 2011-02-11T07:23:19+00:00
author: admin
layout: post
guid: http://www.shootsoft.net/?p=110
categories:
  - MySQL
tags:
  - "1175"
  - 'Error Code: 1175'
  - MySQL
  - Workbench
  - 批量删除
  - 批量更新
---
<p style="margin: 0in; font-size: 11.0pt;">
  <span style="font-family: 宋体;" lang="zh-CN">今日用</span><span style="font-family: Calibri;" lang="en-US">MySQL Workbench</span><span style="font-family: 宋体;" lang="zh-CN">进行数据库的管理更新时，执行一个更新的语句碰到以下错误提示：</span>
</p>

> <p style="margin: 0in; font-family: Calibri; font-size: 11.0pt;">
>   Error Code: 1175
> </p>
> 
> <p style="margin: 0in; font-family: Calibri; font-size: 11.0pt;">
>   You are using safe update mode and you tried to update a table without a WHERE that uses a KEY column
> </p>

<p style="margin: 0in; font-family: Calibri; font-size: 11.0pt;">
  <p style="margin: 0in; font-size: 11.0pt;">
    <span style="font-family: 宋体;" lang="zh-CN">进过一番搜索之后发现原来是</span><span style="font-family: Calibri;" lang="en-US">MySQL Workbench</span><span style="font-family: 宋体;" lang="zh-CN">的安全设置。当要执行的</span><span style="font-family: Calibri;" lang="en-US">SQL</span><span style="font-family: 宋体;" lang="zh-CN">语句是进行批量更新或者删除的时候就会提示这个错误。</span>
  </p>
  
  <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
    <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
      解决方法如下：
    </p>
    
    <ul>
      <li>
        <span style="font-family: 宋体;" lang="zh-CN">打开</span><span style="font-family: Calibri;" lang="en-US">Workbench</span><span style="font-family: 宋体;" lang="zh-CN">的菜单</span><span style="font-family: Calibri;" lang="en-US">[Edit]->[Preferences&#8230;]</span>
      </li>
      <li>
        <span style="font-family: 宋体;" lang="zh-CN">切换到</span><span style="font-family: Calibri;" lang="en-US">[SQL Editor]</span><span style="font-family: 宋体;" lang="zh-CN">页面</span>
      </li>
      <li>
        <span style="font-family: 宋体;" lang="zh-CN">把</span><span style="font-family: Calibri;" lang="en-US">[Forbid UPDATE and DELETE statements without a WHERE clause (safe updates)]</span><span style="font-family: 宋体;" lang="zh-CN">之前的对勾去掉</span>
      </li>
      <li>
        <span style="font-family: 宋体;" lang="zh-CN">点击</span><span style="font-family: Calibri;" lang="en-US">[OK]</span><span style="font-family: 宋体;" lang="zh-CN">按钮</span>
      </li>
      <li>
        <span style="font-family: 宋体;">最后一步记得要重启一下Workbench，否则你仍然会得到这个错误提示。</span>
      </li>
    </ul>
    
    <p style="margin: 0in; font-size: 11.0pt;">
      <span style="font-family: 宋体;" lang="zh-CN"><br /> </span>
    </p>
    
    <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
      <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
        如下图：
      </p>
      
      <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
        <p style="margin: 0in; font-family: 宋体; font-size: 11.0pt;">
          <p style="margin: 0in; font-size: 11.0pt;">
            <a href="http://www.shootsoft.net/wp-content/uploads/2011/02/workbench_preferences.png"><img class="alignnone size-medium wp-image-111" title="workbench_preferences" src="http://www.shootsoft.net/wp-content/uploads/2011/02/workbench_preferences-300x255.png" alt="" width="300" height="255" srcset="https://www.shootsoft.net/wp-content/uploads/2011/02/workbench_preferences-300x255.png 300w, https://www.shootsoft.net/wp-content/uploads/2011/02/workbench_preferences.png 700w" sizes="(max-width: 300px) 100vw, 300px" /></a>
          </p>
          
          <p style="margin: 0in; font-size: 11.0pt;">
            <p style="margin: 0in; font-size: 11.0pt;">
              <p style="margin: 0in; font-size: 11.0pt;">
                <p style="margin: 0in; font-size: 11.0pt;">
                  <p style="margin: 0in; font-size: 11.0pt;">
                    <span style="font-family: 宋体;" lang="zh-CN">再次运行</span><span style="font-family: Calibri;" lang="en-US">SQL</span><span style="font-family: 宋体;" lang="zh-CN">语句就没问题了</span>
                  </p>