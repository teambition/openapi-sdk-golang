# Teambition Openapi SDK

### 安装

```shell
go get github.com/teambition/tb-oapi-go-sdk
```

## 如何使用

### API 调用示例

```go
package main

import (
	"context"
	openapiclient "github.com/teambition/tb-oapi-go-sdk"
	"log"
)

var appId string = "YOU_APP_ID"
var appSecret string = "YOU_APP_SECRET"
var orgId string = "YOU_ORG_ID"
var basePath string = "https://open.teambition.com/api"

func main() {
	cfg := openapiclient.NewConfiguration(appId, appSecret)

	// 设置 api 地址，如果不填默认为 "https://open.teambition.com/api"
	cfg.BasePath = basePath

	client := openapiclient.NewAPIClient(cfg)

	ctx, cancel := context.WithTimeout(context.Background(), time.Second*3)

	res, httpRes, err := client.OrgAPI.GetOrgInfo(ctx).XTenantId(orgId).Execute()
	log.Println(res, httpRes, err)

	cancel()
}

````
### API 接口文档

所有 URI 都相对于 *https://open.teambition.com/api*

类名 | 方法 | HTTP 请求 | 描述
------------ | ------------- | ------------- | -------------
*AppAPI* | [**CheckUserVisibleInApp**](https://open.teambition.com/docs/apis/6321c6cd912d20d3b5a4884b) | **Post** /user/app/exists | 批量查询用户应用可见性
*AppAPI* | [**GetAppAccessToken**](https://open.teambition.com/docs/apis/6687ac14c35daba54d25e578) | **Post** /appToken | 获取应用授权Token
*AutoflowAPI* | [**TriggerCustomEvent**](https://open.teambition.com/docs/apis/6527b37e912d20d3b57881d3) | **Post** /autoflow/custom-event/trigger | 触发自动化自定义事件
*CodeAPI* | [**CreatePlatform**](https://open.teambition.com/docs/apis/642699d77a073e002ba6fa26) | **Post** /code/pipeline/platforms | 创建流水线源平台
*CodeAPI* | [**GetPipeline**](https://open.teambition.com/docs/apis/63f868a65e4331002ae93af8) | **Get** /code/pipeline/get/{platformId} | 根据code查询流水线
*CodeAPI* | [**GetPipelinePlatform**](https://open.teambition.com/docs/apis/63f826f54493a7002b2b459e) | **Get** /code/platform/get | 根据名称查询流水线源平台
*CodeAPI* | [**GetPlatforms**](https://open.teambition.com/docs/apis/642697f07a073e002ba6f4b9) | **Get** /code/pipeline/platforms | 查询流水线源平台
*CodeAPI* | [**SyncBuilds**](https://open.teambition.com/docs/apis/64269d517a073e002ba703e2) | **Post** /code/pipeline/platforms/{platformId}/pipelines/{pipelineId}/builds | 同步构建信息
*CodeAPI* | [**SyncPipelines**](https://open.teambition.com/docs/apis/64269bdd7a073e002ba6fdf0) | **Post** /code/pipeline/platforms/{platformId}/pipelines | 同步流水线信息
*CodeAPI* | [**UpdatePipelineParams**](https://open.teambition.com/docs/apis/63f865b05e4331002ae92888) | **Post** /code/pipeline/platforms/{platformId}/pipelines/{pipelineId}/buildParams | 同步流水线构建参数信息
*CodeAPI* | [**UpdatePipelinePlatform**](https://open.teambition.com/docs/apis/63f822db4493a7002b2b384f) | **Post** /code/platform/update/{platformId} | 更新流水线源平台
*ContactAPI* | [**AddDepartmentMembers**](https://open.teambition.com/docs/apis/667d5158912d20d3b5b76029) | **Post** /org/department/members | 添加部门成员
*ContactAPI* | [**BatchGetOrgMembers**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48b59) | **Post** /org/member/batchGet | 批量获取企业成员
*ContactAPI* | [**CountOrgMembers**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48b29) | **Get** /org/member/count | 获取企业成员数量
*ContactAPI* | [**CreateDepartment**](https://open.teambition.com/docs/apis/632828c3912d20d3b5aca5ab) | **Post** /org/department/create | 创建部门
*ContactAPI* | [**CreateOrgRole**](https://open.teambition.com/docs/apis/67d275d8713c85f499e9437c) | **Post** /org/organizations/{organizationId}/role/create | 创建企业角色
*ContactAPI* | [**DeleteDepartment**](https://open.teambition.com/docs/apis/632828c3912d20d3b5aca62a) | **Delete** /org/department/delete | 删除部门
*ContactAPI* | [**DeleteOrgMember**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48afb) | **Post** /org/member/delete | 删除企业成员
*ContactAPI* | [**DisableOrgMember**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48abe) | **Post** /org/member/disable | 停用企业成员账号
*ContactAPI* | [**EnableOrgMember**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48a8e) | **Post** /org/member/enable | 启用企业成员账号
*ContactAPI* | [**GetDepartment**](https://open.teambition.com/docs/apis/632828c3912d20d3b5aca571) | **Get** /org/department/info | 获取部门详情
*ContactAPI* | [**GetRoleInfo**](https://open.teambition.com/docs/apis/64d34c89912d20d3b54f029c) | **Get** /org/role/info | 获取角色详情
*ContactAPI* | [**ListDepartmentMembers**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48bfc) | **Get** /org/department/members | 获取部门成员列表
*ContactAPI* | [**ListDepartments**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48bbc) | **Get** /org/departments | 获取企业部门列表
*ContactAPI* | [**ListOrgAdmins**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48974) | **Get** /org/admins | 获取企业的管理员（含拥有者）
*ContactAPI* | [**ListOrgMembers**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a489ee) | **Get** /org/member/list | 获取企业成员列表
*ContactAPI* | [**ListOrgOwners**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a489be) | **Get** /org/owners | 获取企业拥有者
*ContactAPI* | [**ListOrgRoles**](https://open.teambition.com/docs/apis/64d34c89912d20d3b54f0373) | **Get** /org/roles | 获取企业角色列表
*ContactAPI* | [**ListSubDepartments**](https://open.teambition.com/docs/apis/667d5158912d20d3b5b75f43) | **Get** /org/departments/subDepts | 获取子部门列表
*ContactAPI* | [**ListUserDepartments**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48c30) | **Get** /user/joinedDepartments | 获取用户加入的企业部门列表
*ContactAPI* | [**RemoveDepartmentMembers**](https://open.teambition.com/docs/apis/667d5159912d20d3b5b76087) | **Delete** /org/department/members | 删除部门成员
*ContactAPI* | [**ResignOrgMember**](https://open.teambition.com/docs/apis/681b514d8657139bff2fe828) | **Post** /org/member/resignation | 离职企业成员账号
*ContactAPI* | [**SearchOrgMembers**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48b88) | **Get** /org/member/search | 搜索企业成员
*ContactAPI* | [**UpdateDepartment**](https://open.teambition.com/docs/apis/632828c3912d20d3b5aca5ed) | **Put** /org/department/update | 更新部门信息
*ContactAPI* | [**UpdateOrgMember**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a48a5b) | **Put** /org/member/update | 更新企业成员
*CustomfieldAPI* | [**CountByCategoryV3**](https://open.teambition.com/docs/apis/63ee3ea2912d20d3b543ee9c) | **Get** /v3/customfield/count-by-category | 根据自定义字段分类统计自定义字段数
*CustomfieldAPI* | [**CreateProjectCustomfieldV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a492ca) | **Post** /v3/customfield/create | 创建项目自定义字段(提交项目ID),创建企业自定义字段
*CustomfieldAPI* | [**DeleteCustomfieldV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a4930c) | **Post** /v3/customfield/{customfieldId}/delete | 删除自定义字段，默认删除企业自定义字段，如果传递项目ID，则删除项目下自定义字段
*CustomfieldAPI* | [**SearchFieldCategoriesV3**](https://open.teambition.com/docs/apis/63ee3ea2912d20d3b543ee57) | **Get** /v3/customfield-category/search | 搜索企业自定义字段分类
*CustomfieldAPI* | [**SearchFieldChoicesV3**](https://open.teambition.com/docs/apis/64057c9b912d20d3b5e63df6) | **Get** /v3/customfield/{customfieldId}/choice/search | 搜索层级字段选项
*CustomfieldAPI* | [**SearchOrgCustomfiledV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49355) | **Get** /v3/customfield/search | 搜索企业自定义字段
*CustomfieldAPI* | [**UpdateCustomfieldV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49391) | **Put** /v3/customfield/{customfieldId}/update | 更新自定义字段，默认更新企业自定义字段，如果传递项目ID，则更新项目下自定义字段
*CustomfieldAPI* | [**UpdateFieldChoicesV3**](https://open.teambition.com/docs/apis/64057c9b912d20d3b5e63e6c) | **Post** /v3/customfield/{customfieldId}/choice/update | 更新层级字段选项
*DingGroupAPI* | [**GetBindingCidByTaskId**](https://open.teambition.com/docs/apis/664c9212e678cdcec87811ba) | **Get** /group/getBindingCidByTaskId | 通过taskId查询该任务关联的任务群Id
*DingGroupAPI* | [**GetBindingCidsByProjectId**](https://open.teambition.com/docs/apis/6378b1e6912d20d3b517bea6) | **Get** /group/getBindingCidsByProjectId | 通过projectid查询关联的全员可见的群聊ids
*DingGroupAPI* | [**GetBindingProjectIdsByCid**](https://open.teambition.com/docs/apis/6378b1e6912d20d3b517bf09) | **Get** /group/getBindingProjectIdsByCid | 根据群聊cid获取绑定的项目projectid
*DingtalkAPI* | [**BindProjectWorkspace**](https://open.teambition.com/docs/apis/65af6cec2442f01adbdedec9) | **Post** /workspace/bind-project | 绑定已有知识库
*DingtalkAPI* | [**GetTaskIdsByApproveId**](https://open.teambition.com/docs/apis/64f5d782a96085002bab6976) | **Get** /approve/getTaskIdsByInstanceId | 通过钉钉审批实例ID反查对应任务IDs
*DingtalkAPI* | [**GetWorkspaceInfo**](https://open.teambition.com/docs/apis/66b9c71e68fd651bec0a05d3) | **Get** /workspace/query | 获取绑定知识库信息
*FileAPI* | [**BatchGetFileDetails**](https://open.teambition.com/docs/apis/65b20e66912d20d3b5781196) | **Post** /v3/file/query/by-resource-ids | 根据 resourceId 批量获取文件详情
*FileAPI* | [**CreateFileV3**](https://open.teambition.com/docs/apis/6411504e912d20d3b56ec570) | **Post** /v3/work/create | 创建文件库文件
*FileAPI* | [**CreateFolderV3**](https://open.teambition.com/docs/apis/64db2903912d20d3b5bb0034) | **Post** /v3/collection/create | 创建文件夹
*FileAPI* | [**CreateUploadTokenV3**](https://open.teambition.com/docs/apis/64114f70912d20d3b56e0c59) | **Post** /v3/awos/upload-token | 创建文件上传凭证
*FileAPI* | [**GetFileDetailV3**](https://open.teambition.com/docs/apis/64db2921912d20d3b5bb5250) | **Get** /v3/work/query | 获取项目文件详情
*FileAPI* | [**GetFileToken**](https://open.teambition.com/docs/apis/65810e45912d20d3b5887d1b) | **Post** /v3/file/file-token | 从现有文件资源创建 fileToken，可用于创建其他文件资源
*FileAPI* | [**GetFolderDetailV3**](https://open.teambition.com/docs/apis/64db2903912d20d3b5bb021f) | **Get** /v3/collection/query | 获取文件夹详情
*FileAPI* | [**ListFilesV3**](https://open.teambition.com/docs/apis/6411504e912d20d3b56ec5ff) | **Get** /v3/work/list | 获取文件列表
*FileAPI* | [**MoveFileV3**](https://open.teambition.com/docs/apis/64db2930912d20d3b5bb7d96) | **Post** /v3/work/{workId}/parent | 项目内移动文件
*FileAPI* | [**MoveFolderV3**](https://open.teambition.com/docs/apis/64db2903912d20d3b5bb00c9) | **Post** /v3/collection/{collectionId}/parent | 移动文件夹
*FileAPI* | [**SearchFilesV3**](https://open.teambition.com/docs/apis/68510bf3912d20d3b5cd319e) | **Get** /v3/work/search | 搜索文件列表
*FileAPI* | [**UpdateFileNameV3**](https://open.teambition.com/docs/apis/64db2930912d20d3b5bb7d17) | **Post** /v3/work/{workId}/name/update | 更新文件标题
*FileAPI* | [**UpdateFileVersionV3**](https://open.teambition.com/docs/apis/64db2930912d20d3b5bb7e0e) | **Post** /v3/work/{workId}/version | 更新文件版本
*FileAPI* | [**UpdateFolderTitleV3**](https://open.teambition.com/docs/apis/64db2903912d20d3b5bb0173) | **Post** /v3/collection/{collectionId}/title/update | 更新文件夹标题
*FileAPI* | [**UpdateFolderVisibility**](https://open.teambition.com/docs/apis/676bb6ff912d20d3b56b8d0f) | **Post** /v3/collection/visible/update | 更新文件夹可见性
*FormAPI* | [**CreateFormRecordV3**](https://open.teambition.com/docs/apis/680b630d912d20d3b51dcf46) | **Post** /v3/form/record/create | 创建表单记录
*FormAPI* | [**GetFormProjectSpaceLinkV3**](https://open.teambition.com/docs/apis/680b630e912d20d3b51dd06d) | **Get** /v3/form/project/link | 根据项目ID获取表单空间或根据表单空间ID获取项目ID
*FormAPI* | [**ListAllFormSpaceNodesV3**](https://open.teambition.com/docs/apis/680b630e912d20d3b51dd0c4) | **Get** /v3/form/node/list | 获取表单空间节点列表
*FormAPI* | [**SearchFormRecordProcessNodesV3**](https://open.teambition.com/docs/apis/6808506d912d20d3b5bfe326) | **Get** /v3/form/record/{recordId}/process/instance/node/search | 获取表单记录流程节点信息
*FormAPI* | [**UpdateFormRecordFieldV3**](https://open.teambition.com/docs/apis/680b630e912d20d3b51dd01c) | **Post** /v3/form/record/{recordId}/update | 更新表单字段值
*GanttAPI* | [**CreateBaseline**](https://open.teambition.com/docs/apis/66b4ae32912d20d3b58405f5) | **Post** /v3/gantt/baseline | 项目下创建甘特图基线
*GanttAPI* | [**GetBaselineTasksV3**](https://open.teambition.com/docs/apis/6424f857912d20d3b50b048a) | **Get** /v3/gantt/baseline-task | 获取甘特图基线下的任务
*GanttAPI* | [**GetBaselinesV3**](https://open.teambition.com/docs/apis/6424f885912d20d3b50b759b) | **Get** /v3/gantt/baseline | 获取项目下甘特图基线
*GanttAPI* | [**UpdateBaseline**](https://open.teambition.com/docs/apis/66d98080253a3f2062f9b838) | **Put** /v3/gantt/baseline | 更新项目下甘特图基线
*GroupAPI* | [**AddGroupMember**](https://open.teambition.com/docs/apis/64d34cb2912d20d3b54f6e39) | **Post** /org/group/member/add | 添加群组成员
*GroupAPI* | [**BatchGetGroupMembers**](https://open.teambition.com/docs/apis/64d34cb2912d20d3b54f6dba) | **Post** /org/group/member/batchGet | 批量获取群组成员
*GroupAPI* | [**BatchGetGroups**](https://open.teambition.com/docs/apis/64d44dbe912d20d3b53a8340) | **Post** /org/group/batchGet | 批量获取群组信息
*GroupAPI* | [**CreateGroup**](https://open.teambition.com/docs/apis/64d34c9c912d20d3b54f33ea) | **Post** /org/group/create | 创建群组
*GroupAPI* | [**DeleteGroup**](https://open.teambition.com/docs/apis/64d34c9c912d20d3b54f34ee) | **Delete** /org/group/delete | 删除群组
*GroupAPI* | [**ListGroupMembers**](https://open.teambition.com/docs/apis/64d34cb2912d20d3b54f6d10) | **Get** /org/group/members | 获取群组成员列表
*GroupAPI* | [**RemoveGroupMember**](https://open.teambition.com/docs/apis/64d34cb2912d20d3b54f6e8d) | **Delete** /org/group/member/delete | 删除群组成员
*GroupAPI* | [**SearchGroups**](https://open.teambition.com/docs/apis/64d34c9c912d20d3b54f3379) | **Get** /org/group/search | 搜索群组
*GroupAPI* | [**UpdateGroup**](https://open.teambition.com/docs/apis/64d34c9c912d20d3b54f3487) | **Put** /org/group/update | 更新群组
*OauthAPI* | [**GetOAuthUserInfo**](https://open.teambition.com/docs/apis/6321c6cd912d20d3b5a487e2) | **Post** /oauth/userInfo | 获取登录用户信息
*OauthAPI* | [**GetSSOToken**](https://open.teambition.com/docs/apis/6321c6cd912d20d3b5a48785) | **Get** /oauth/sso | 请求身份验证
*OauthAPI* | [**GetUserAccessToken**](https://open.teambition.com/docs/apis/6321c6cd912d20d3b5a487bd) | **Post** /oauth/userAccessToken | 获取登录用户身份
*OrgAPI* | [**GetAuditLogs**](https://open.teambition.com/docs/apis/6620e7e6912d20d3b551cda8) | **Get** /audit-log/list | 获取企业审计日志
*OrgAPI* | [**GetDingCorpId**](https://open.teambition.com/docs/apis/66792847912d20d3b5161000) | **Get** /idmap/dingtalk/getCorpId | 查询企业绑定的钉钉 CorpId
*OrgAPI* | [**GetDingUserIdByTbUserId**](https://open.teambition.com/docs/apis/66792847912d20d3b5160f7d) | **Get** /idmap/dingtalk/getDingUserId | Teambition userId 查询钉钉 userId
*OrgAPI* | [**GetOrgInfo**](https://open.teambition.com/docs/apis/6321c6ce912d20d3b5a488f4) | **Get** /org/info | 获取企业信息
*OrgAPI* | [**GetTbUserIdByDingUserId**](https://open.teambition.com/docs/apis/66792847912d20d3b5160f10) | **Get** /idmap/dingtalk/getTbUserId | 钉钉 userId 查询 Teambition userId
*OrgAPI* | [**ListLicenseAllocations**](https://open.teambition.com/docs/apis/6364d27b912d20d3b5f654a5) | **Get** /seat/member/allocated | 获取License名额分配列表
*ProgramAPI* | [**AddProgramMembersV3**](https://open.teambition.com/docs/apis/66693d96912d20d3b5ee560b) | **Post** /v3/program/{programId}/member/create | 批量添加成员到项目集
*ProgramAPI* | [**AddProgramProjectsV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa74a) | **Post** /v3/program/{programId}/project/create | 批量添加项目到项目集
*ProgramAPI* | [**CreateProgramStatusCustomFieldV3**](https://open.teambition.com/docs/apis/66e00a72912d20d3b5a1572b) | **Post** /v3/program/{programId}/status/customfield/create | 更新项目集概览自定义字段值
*ProgramAPI* | [**CreateProgramStatusV3**](https://open.teambition.com/docs/apis/66e00a72912d20d3b5a15688) | **Post** /v3/program/{programId}/status/create | 创建项目集状态
*ProgramAPI* | [**CreateProgramV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa614) | **Post** /v3/program/create | 创建项目集
*ProgramAPI* | [**DeleteProgramStatusCustomFieldV3**](https://open.teambition.com/docs/apis/66e00a72912d20d3b5a1578a) | **Post** /v3/program/{programId}/status/customfield/delete | 删除项目集概览自定义字段
*ProgramAPI* | [**DeleteProgramStatusV3**](https://open.teambition.com/docs/apis/66e00a72912d20d3b5a15875) | **Post** /v3/program/{programId}/status/delete | 删除项目集状态
*ProgramAPI* | [**DeleteProgramV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa695) | **Post** /v3/program/{programId}/delete | 删除项目集
*ProgramAPI* | [**GetProgramsV3**](https://open.teambition.com/docs/apis/6501ad17912d20d3b5086630) | **Get** /v3/program/query | 查询项目集
*ProgramAPI* | [**ListProgramMembersV3**](https://open.teambition.com/docs/apis/66693d96912d20d3b5ee5737) | **Get** /v3/program/{programId}/member | 查询项目集内成员
*ProgramAPI* | [**ListProgramProjectsV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa85c) | **Get** /v3/program/{programId}/projects | 查询项目集内项目
*ProgramAPI* | [**ListProgramStatusCustomFieldsV3**](https://open.teambition.com/docs/apis/66e00a72912d20d3b5a157f5) | **Get** /v3/program/{programId}/status/customfield/list | 查询项目集概览自定义字段列表
*ProgramAPI* | [**ListProgramStatusesV3**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a158dd) | **Get** /v3/program/{programId}/status/list | 查询项目集状态和状态历史
*ProgramAPI* | [**RemoveProgramMembersV3**](https://open.teambition.com/docs/apis/66693d96912d20d3b5ee56af) | **Post** /v3/program/{programId}/member/delete | 批量删除项目集内的成员
*ProgramAPI* | [**RemoveProgramProjectV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa7d3) | **Post** /v3/program/{programId}/project/{projectId}/delete | 删除项目集内的项目
*ProjectAPI* | [**AddProjectGroupMemberV3**](https://open.teambition.com/docs/apis/6646e45a912d20d3b576c2f0) | **Post** /v3/project-tag/{projectTagId}/member/create | 创建项目分组成员
*ProjectAPI* | [**AddProjectMembersV3**](https://open.teambition.com/docs/apis/6363bcfa912d20d3b56faf07) | **Post** /v3/project/{projectId}/member/create-v2 | 创建项目成员 v2
*ProjectAPI* | [**ArchiveProjectV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a496ed) | **Post** /v3/project/{projectId}/archive | 项目放入回收站
*ProjectAPI* | [**AssignMemberRoleV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49942) | **Post** /v3/project/{projectId}/member/role/assign | 修改项目成员的角色
*ProjectAPI* | [**BatchGetProjectCustomFiledByInstanceIdsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a497b9) | **Get** /v3/project/{projectId}/customfield/get-by-instance | 批量根据instanceId查询字段
*ProjectAPI* | [**CompleteSprintV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b9231) | **Put** /v3/project/{projectId}/sprint/{sprintId}/complete | 完成迭代
*ProjectAPI* | [**CopyProjectAsyncV3**](https://open.teambition.com/docs/apis/64e810ff912d20d3b58fa8bc) | **Post** /v3/project/{projectId}/copy-async | 异步复制项目
*ProjectAPI* | [**CopyProjectV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49724) | **Post** /v3/project/{projectId}/copy | 复制项目
*ProjectAPI* | [**CountProjectTasksV3**](https://open.teambition.com/docs/apis/6646e45a912d20d3b576c01a) | **Get** /v3/project/{projectId}/task/count | 计数项目任务
*ProjectAPI* | [**CreateBugGroup**](https://open.teambition.com/docs/apis/682c1944912d20d3b5a29c8c) | **Post** /v3/project/{projectId}/bug/commongroup/create | 创建缺陷分类
*ProjectAPI* | [**CreateOrgProjectRoleV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a356) | **Post** /v3/project-role/create | 创建企业后台项目角色
*ProjectAPI* | [**CreateProjectFromTemplateV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49753) | **Post** /v3/project/create-from-template | 从模板创建项目
*ProjectAPI* | [**CreateProjectGroupV3**](https://open.teambition.com/docs/apis/6363b54f912d20d3b567d83b) | **Post** /v3/project-tag/create | 创建项目分组
*ProjectAPI* | [**CreateProjectLinkV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a499a5) | **Post** /v3/project/{projectId}/objectlinks | 创建项目关联
*ProjectAPI* | [**CreateProjectMemberV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a498c0) | **Post** /v3/project/{projectId}/member/create | 创建项目成员(弃用)
*ProjectAPI* | [**CreateProjectRoleV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49b28) | **Post** /v3/project/{projectId}/role/create | 创建项目角色
*ProjectAPI* | [**CreateProjectStatusV3**](https://open.teambition.com/docs/apis/63e2387a912d20d3b5d3fe38) | **Post** /v3/project/{projectId}/status/create | 创建项目状态
*ProjectAPI* | [**CreateProjectTagV3**](https://open.teambition.com/docs/apis/63e2386b912d20d3b5d3ef64) | **Post** /v3/project/{projectId}/tag/create | 创建项目标签
*ProjectAPI* | [**CreateProjectTemplateV3**](https://open.teambition.com/docs/apis/66431ec5912d20d3b5436e4c) | **Post** /v3/project-template/create | 创建项目模版
*ProjectAPI* | [**CreateProjectV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49780) | **Post** /v3/project/create | 创建项目
*ProjectAPI* | [**CreateRoleFromTemplateV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49ae8) | **Post** /v3/project/{projectId}/role/create-by-project-role | 引入企业后台项目角色到项目
*ProjectAPI* | [**CreateSprintV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b92b9) | **Post** /v3/project/{projectId}/sprint/create | 创建迭代
*ProjectAPI* | [**CreateStatusCustomFieldV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49d3f) | **Post** /v3/project/{projectId}/status/customfield/create | 更新项目概览自定义字段值
*ProjectAPI* | [**CreateStoryGroup**](https://open.teambition.com/docs/apis/682c1948912d20d3b5a2b50e) | **Post** /v3/project/{projectId}/story/commongroup/create | 创建需求分类
*ProjectAPI* | [**CreateTaskGroupV3**](https://open.teambition.com/docs/apis/64264d40912d20d3b58848b3) | **Post** /v3/project/{projectId}/tasklist/create | 创建任务分组
*ProjectAPI* | [**CreateTaskStageV3**](https://open.teambition.com/docs/apis/64264d40912d20d3b5884608) | **Post** /v3/project/{projectId}/stage/create | 创建任务列表
*ProjectAPI* | [**CreateTaskflowStatusV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a003) | **Post** /v3/project/{projectId}/taskflowstatus/create | 创建项目工作流状态
*ProjectAPI* | [**CreateTaskflowV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49ef9) | **Post** /v3/project/{projectId}/taskflow/create | 创建项目工作流
*ProjectAPI* | [**CreateTestPlan**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a92e) | **Post** /v3/project/{projectId}/testplan/create | 创建测试计划
*ProjectAPI* | [**CreateTestPlanGroup**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a886) | **Post** /v3/project/{projectId}/testplan/{testplanId}/commongroup/create | 创建测试计划分组
*ProjectAPI* | [**DeleteOrgProjectRoleV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a399) | **Post** /v3/project-role/{roleId}/delete | 删除企业后台项目角色
*ProjectAPI* | [**DeleteProjectGroupV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb3b4) | **Delete** /v3/project-tag/{projectTagId} | 删除项目分组
*ProjectAPI* | [**DeleteProjectLinkV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a499df) | **Delete** /v3/project/{projectId}/objectlinks/{objectlinkId} | 删除项目关联
*ProjectAPI* | [**DeleteProjectMemberV3**](https://open.teambition.com/docs/apis/63e23a3e912d20d3b5d599a8) | **Post** /v3/project/{projectId}/member/delete | 删除项目成员
*ProjectAPI* | [**DeleteProjectRoleV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49b61) | **Post** /v3/project/{projectId}/role/{roleId}/delete | 移除项目角色
*ProjectAPI* | [**DeleteProjectTemplateV3**](https://open.teambition.com/docs/apis/6643341a912d20d3b58ebb5e) | **Delete** /v3/project-template/{templateId} | 删除项目模版
*ProjectAPI* | [**DeleteProjectV3**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a1593b) | **Post** /v3/project/{projectId}/delete | 删除项目
*ProjectAPI* | [**DeleteSprintV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b9340) | **Post** /v3/project/{projectId}/sprint/{sprintId}/delete | 删除迭代
*ProjectAPI* | [**DeleteStatusCustomFieldV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49d6f) | **Post** /v3/project/{projectId}/status/customfield/{customfieldId}/delete | 删除项目概览自定义字段(弃用)
*ProjectAPI* | [**DeleteTaskFlowStatusV3**](https://open.teambition.com/docs/apis/6437eaa1912d20d3b5685875) | **Post** /v3/project/{projectId}/taskflowstatus/{tfsId}/delete | 删除项目工作流状态
*ProjectAPI* | [**DeleteTaskflowV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49f36) | **Post** /v3/project/{projectId}/taskflow/{taskflowId}/delete | 删除项目工作流
*ProjectAPI* | [**GetAsyncJobResultV3**](https://open.teambition.com/docs/apis/6501ad12912d20d3b50846fc) | **Get** /v3/async-job/list | 获取异步 job 执行结果
*ProjectAPI* | [**GetMemberRolesV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fafcb) | **Get** /v3/project/{projectId}/member-role | 获取项目成员角色（包含权限穿透角色）
*ProjectAPI* | [**GetProjectLinksV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a4996f) | **Get** /v3/project/{projectId}/objectlinks | 获取项目关联列表
*ProjectAPI* | [**GetProjectOrgChart**](https://open.teambition.com/docs/apis/6808506d912d20d3b5bfe3a5) | **Get** /v3/project/{projectId}/preference/project-team | 获取项目组织架构图
*ProjectAPI* | [**GetProjectProgram**](https://open.teambition.com/docs/apis/67d0f72e912d20d3b5f09e35) | **Get** /v3/project/{projectId}/program/query | 查询项目所属项目集id
*ProjectAPI* | [**GetProjectTableCustomField**](https://open.teambition.com/docs/apis/682c18da912d20d3b5a16e8c) | **Get** /v3/project/{projectId}/customfield/table | 获取项目的表格自定义字段
*ProjectAPI* | [**GetProjectTagsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49a2e) | **Get** /v3/project/{projectId}/project-tag | 查看项目的项目分组
*ProjectAPI* | [**GetScenarioFieldsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49cc4) | **Get** /v3/project/{projectId}/scenariofieldconfig/search | 获取项目任务类型
*ProjectAPI* | [**GetTestCaseGroupMappings**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a1b6) | **Get** /v3/project/{projectId}/testcase/commongroup-mapping | 批量获取测试用例与归属分组的对应关系
*ProjectAPI* | [**InstallProjectAppV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49662) | **Post** /v3/project/{projectId}/application/{appId}/create | 安装项目应用
*ProjectAPI* | [**ListBugGroups**](https://open.teambition.com/docs/apis/66b4ae32912d20d3b5840871) | **Get** /v3/project/{projectId}/bug/commongroup | 获取缺陷分类列表
*ProjectAPI* | [**ListOrgProjectRolesV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a3d2) | **Get** /v3/project-role/list | 获取企业后台项目角色
*ProjectAPI* | [**ListPrioritiesV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a4961c) | **Get** /v3/project/priority/list | 查询企业优先级
*ProjectAPI* | [**ListProjectAppsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a496c1) | **Get** /v3/project/{projectId}/application/list | 查询项目应用列表
*ProjectAPI* | [**ListProjectGroupMembersV3**](https://open.teambition.com/docs/apis/6646e45a912d20d3b576c3fd) | **Get** /v3/project-tag/{projectTagId}/member/list | 获取项目分组成员列表
*ProjectAPI* | [**ListProjectMembersV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49906) | **Get** /v3/project/{projectId}/member | 获取项目成员列表
*ProjectAPI* | [**ListProjectRemindersV3**](https://open.teambition.com/docs/apis/63292c59912d20d3b5da9e3c) | **Get** /v3/project/{projectId}/reminder/list | 获取项目「默认任务提醒」列表
*ProjectAPI* | [**ListProjectRolesV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49b8f) | **Get** /v3/project/{projectId}/role | 获取项目角色列表
*ProjectAPI* | [**ListProjectStatusesV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49dd1) | **Get** /v3/project/{projectId}/status/list | 查询项目状态和状态历史
*ProjectAPI* | [**ListStarredProjects**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a15a91) | **Get** /v3/project-star/query | 查询用户星标项目
*ProjectAPI* | [**ListStatusCustomFieldsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49d9d) | **Get** /v3/project/{projectId}/status/customfield/list | 查询项目概览自定义字段列表
*ProjectAPI* | [**ListStatusExecutorsV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb176) | **Get** /v3/project/{projectId}/taskflowstatus/{tfsId}/executor/list | 列出项目工作流状态流转执行角色列表
*ProjectAPI* | [**ListStatusFieldGroupsV3**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a15b19) | **Get** /v3/project/{projectId}/status/field-group/list | 查询项目概览字段分组列表
*ProjectAPI* | [**ListStatusValidatorsV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb20e) | **Get** /v3/project/{projectId}/taskflowstatus/{tfsId}/validator/list | 列出项目工作流状态流转校验列表
*ProjectAPI* | [**ListStoryGroupsV3**](https://open.teambition.com/docs/apis/6360900d912d20d3b5bb02a6) | **Get** /v3/project/{projectId}/story/commongroup | 获取需求分类列表
*ProjectAPI* | [**ListTestPlanGroups**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a8f1) | **Get** /v3/project/{projectId}/testplan/{testplanId}/commongroup | 获取测试计划分组列表
*ProjectAPI* | [**ListTestPlans**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a996) | **Get** /v3/project/{projectId}/testplan | 获取测试计划
*ProjectAPI* | [**ListUserProjectsV3**](https://open.teambition.com/docs/apis/6321c912912d20d3b5a6beb7) | **Get** /v3/project/user-joined | 获取用户参与项目
*ProjectAPI* | [**MoveTaskFlowStatusV3**](https://open.teambition.com/docs/apis/6437eaa1912d20d3b5685947) | **Put** /v3/project/{projectId}/taskflowstatus/{tfsId}/move | 更新项目工作流状态位置
*ProjectAPI* | [**QueryGroupProjects**](https://open.teambition.com/docs/apis/66600ca7912d20d3b57431b0) | **Get** /v3/project-tag/{projectTagId}/project/query | 根据项目分组 ID 查询项目
*ProjectAPI* | [**QueryProjectGroupsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a2c7) | **Get** /v3/project-tag/query | 查询项目分组
*ProjectAPI* | [**QueryProjectsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49aa7) | **Get** /v3/project/query | 查询项目
*ProjectAPI* | [**QueryTestPlanGroups**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a8bf) | **Get** /v3/project/{projectId}/commongroup/query | 查询测试计划分组
*ProjectAPI* | [**QueryTestPlans**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a96a) | **Get** /v3/project/{projectId}/testplan/query | 查询测试计划
*ProjectAPI* | [**RemoveProjectGroupMemberV3**](https://open.teambition.com/docs/apis/664ffdf1912d20d3b5897a22) | **Post** /v3/project-tag/{projectTagId}/member/delete | 删除项目分组成员
*ProjectAPI* | [**RemoveStatusCustomFieldV3**](https://open.teambition.com/docs/apis/637f7783912d20d3b5886bf1) | **Post** /v3/project/{projectId}/status/customfield/delete | 删除项目概览自定义字段
*ProjectAPI* | [**RestartSprintV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b94d3) | **Put** /v3/project/{projectId}/sprint/{sprintId}/restart | 重新开始迭代
*ProjectAPI* | [**RestoreProjectV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49e13) | **Post** /v3/project/{projectId}/suspend-restore | 恢复归档项目
*ProjectAPI* | [**SearchOrgTaskFlowStatusesV3**](https://open.teambition.com/docs/apis/6593c8ee912d20d3b5cd6c75) | **Get** /v3/tfs/search | 搜索企业工作流状态
*ProjectAPI* | [**SearchProjectCustomFiledsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a497f6) | **Get** /v3/project/{projectId}/customfield/search | 搜索项目自定义字段
*ProjectAPI* | [**SearchProjectTagsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49e83) | **Get** /v3/project/{projectId}/tag/search | 搜索项目标签
*ProjectAPI* | [**SearchProjectTasksV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49ec1) | **Get** /v3/project/{projectId}/task/query | 查询项目任务
*ProjectAPI* | [**SearchProjectTemplatesV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a30f) | **Get** /v3/project-template/search | 搜索企业项目模板
*ProjectAPI* | [**SearchProjectsTQL**](https://open.teambition.com/docs/apis/6728570f912d20d3b53ed2ea) | **Get** /project/search | 通过TQL搜索项目
*ProjectAPI* | [**SearchSprintsV3**](https://open.teambition.com/docs/apis/6397f1dc912d20d3b572dc9d) | **Get** /v3/project/{projectId}/sprint/search | 迭代搜索
*ProjectAPI* | [**SearchStagesV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb13f) | **Get** /v3/project/{projectId}/stage/search | 搜索任务列表
*ProjectAPI* | [**SearchTaskGroupsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a17d) | **Get** /v3/project/{projectId}/tasklist/search | 搜索任务分组
*ProjectAPI* | [**SearchTaskflowNodes**](https://open.teambition.com/docs/apis/682c1944912d20d3b5a299b2) | **Get** /v3/project/{projectId}/taskflow/node/search | 搜索项目工作流节点
*ProjectAPI* | [**SearchTaskflowStatusesV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a142) | **Get** /v3/project/{projectId}/taskflowstatus/search | 搜索项目工作流状态
*ProjectAPI* | [**SearchTaskflowsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49fc3) | **Get** /v3/project/{projectId}/taskflow/search | 搜索项目工作流
*ProjectAPI* | [**StarProject**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a159e2) | **Post** /v3/project-star/create | 创建用户星标项目
*ProjectAPI* | [**StartSprintV3**](https://open.teambition.com/docs/apis/63a08189912d20d3b56b9593) | **Put** /v3/project/{projectId}/sprint/{sprintId}/start | 开始迭代
*ProjectAPI* | [**SuspendProjectV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49e41) | **Post** /v3/project/{projectId}/suspend | 归档项目
*ProjectAPI* | [**UninstallProjectAppV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49691) | **Post** /v3/project/{projectId}/application/{appId}/delete | 删除项目应用
*ProjectAPI* | [**UpdateOrgProjectRoleV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a40e) | **Post** /v3/project-role/{roleId} | 更新企业后台项目角色
*ProjectAPI* | [**UpdateProjectCode**](https://open.teambition.com/docs/apis/6808506d912d20d3b5bfe486) | **Put** /v3/project/{projectId}/unique-id-prefix | 更新项目编号
*ProjectAPI* | [**UpdateProjectCustomFieldPosition**](https://open.teambition.com/docs/apis/671f8c7fff36bd665c8084cb) | **Put** /v3/project/{projectId}/customfieldLink/{customfieldLinkId}/pos | 更新项目概览自定义字段位置
*ProjectAPI* | [**UpdateProjectGroupMemberPermissionV3**](https://open.teambition.com/docs/apis/664ffdf1912d20d3b5897b32) | **Post** /v3/project-tag/{projectTagId}/member/permissions/update | 更新项目分组成员权限
*ProjectAPI* | [**UpdateProjectGroupV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb36f) | **Put** /v3/project-tag/{projectTagId} | 修改项目分组
*ProjectAPI* | [**UpdateProjectTableCustomField**](https://open.teambition.com/docs/apis/682c18da912d20d3b5a16eea) | **Put** /v3/project/{projectId}/customfield/table | 更新项目的表格自定义字段
*ProjectAPI* | [**UpdateProjectTagsV3**](https://open.teambition.com/docs/apis/6321c6d0912d20d3b5a49a5c) | **Put** /v3/project/{projectId}/project-tag | 更新项目的项目分组
*ProjectAPI* | [**UpdateProjectTemplateInfoV3**](https://open.teambition.com/docs/apis/66693d97912d20d3b5ee5e9c) | **Put** /v3/project-template/{projectTemplateId} | 修改项目模板基本信息
*ProjectAPI* | [**UpdateProjectV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a287) | **Put** /v3/project/{projectId} | 更新项目
*ProjectAPI* | [**UpdateRolePermissionsV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49bca) | **Post** /v3/project/{projectId}/role/{roleId}/permission/update | 修改项目角色的权限项
*ProjectAPI* | [**UpdateSprintLabelV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b93a6) | **Put** /v3/project/{projectId}/sprint/{sprintId}/label/update | 迭代标签更新
*ProjectAPI* | [**UpdateSprintLockV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b940a) | **Put** /v3/project/{projectId}/sprint/{sprintId}/lock/update | 迭代锁定
*ProjectAPI* | [**UpdateSprintPayloadV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b946d) | **Put** /v3/project/{projectId}/sprint/{sprintId}/payload/update | 迭代操作限制更新
*ProjectAPI* | [**UpdateSprintV3**](https://open.teambition.com/docs/apis/63a08189912d20d3b56b95f6) | **Put** /v3/project/{projectId}/sprint/{sprintId}/update | 迭代更新
*ProjectAPI* | [**UpdateStatusCustomFieldV3**](https://open.teambition.com/docs/apis/677b650d912d20d3b5330978) | **Post** /v3/project/{projectId}/status/customfield/update | 更新项目概览自定义字段
*ProjectAPI* | [**UpdateStatusExecutorsV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb1ac) | **Post** /v3/project/{projectId}/taskflowstatus/{tfsId}/executor/update | 更新项目工作流状态流转角色列表
*ProjectAPI* | [**UpdateStatusFieldGroupsV3**](https://open.teambition.com/docs/apis/66e00a73912d20d3b5a15ba2) | **Put** /v3/project/{projectId}/status/field-group | 更新项目概览字段分组列表
*ProjectAPI* | [**UpdateStatusValidatorsV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb244) | **Post** /v3/project/{projectId}/taskflowstatus/{tfsId}/validator/update | 更新项目工作流状态流转校验列表
*ProjectAPI* | [**UpdateTaskFlowRejectStatusV3**](https://open.teambition.com/docs/apis/6437eaa1912d20d3b5685a00) | **Put** /v3/project/{projectId}/taskflowstatus/{tfsId}/rejectstatus | 更新项目工作流状态流转列表
*ProjectAPI* | [**UpdateTaskFlowStatusNameV3**](https://open.teambition.com/docs/apis/6437eaa1912d20d3b56859a4) | **Put** /v3/project/{projectId}/taskflowstatus/{tfsId}/name | 更新项目工作流状态名字
*ProjectAPI* | [**UpdateTaskFlowStatusTypeV3**](https://open.teambition.com/docs/apis/6437eaa1912d20d3b56858e6) | **Put** /v3/project/{projectId}/taskflowstatus/{tfsId}/kind | 更新项目工作流状态
*ProjectAPI* | [**UpdateTaskGroupTitleV3**](https://open.teambition.com/docs/apis/64264d43912d20d3b588593e) | **Put** /v3/project/{projectId}/tasklist/{tasklistId}/title | 更新任务分组名称
*ProjectAPI* | [**UpdateTaskStageNameV3**](https://open.teambition.com/docs/apis/64264d43912d20d3b588580a) | **Put** /v3/project/{projectId}/stage/{stageId}/name | 更新任务列表名称
*ProjectAPI* | [**UpdateTaskflowNameV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49f80) | **Put** /v3/project/{projectId}/taskflow/{taskflowId}/name | 更新项目工作流
*ProjectAPI* | [**UpdateTestCaseGroup**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a1f2) | **Post** /v3/project/{projectId}/testcase/{testcaseId}/commongroup | 更新项目级测试用例分组
*ProjectplanAPI* | [**CreatePlanApprovalV3**](https://open.teambition.com/docs/apis/67f36da38657139bff2bdd65) | **Post** /v3/projectplan/plans/{projectPlanId}/approve | 创建计划审批信息
*ProjectplanAPI* | [**CreateProjectPlanStatusSettingV3**](https://open.teambition.com/docs/apis/67dd2f378657139bff29cf9c) | **Post** /v3/projectplan/projects/{projectId}/planCustomStatusSetting | 配置项目级计划自定义状态信息
*ProjectplanAPI* | [**ExecutePlanEventV3**](https://open.teambition.com/docs/apis/67f36bbb8657139bff2bd260) | **Put** /v3/projectplan/plans/{projectPlanId}/execute/{event} | 更改计划状态
*ProjectplanAPI* | [**GetPlanStatusV3**](https://open.teambition.com/docs/apis/67dd0bd08657139bff298e21) | **Get** /v3/projectplan/plans/{projectPlanId}/status-info | 查询计划状态信息
*ProjectplanAPI* | [**GetPlanV3**](https://open.teambition.com/docs/apis/67dab418a30a3554a5fa69a2) | **Get** /v3/projectplan/plans/{projectPlanId}/query | 查询计划
*ProjectplanAPI* | [**GetProjectPlanStatusSettingV3**](https://open.teambition.com/docs/apis/67dd27bc8657139bff29b100) | **Get** /v3/projectplan/projects/{projectId}/planCustomStatusSetting | 获取项目级计划自定义状态配置
*ProjectplanAPI* | [**ListPlanMemberRolesV3**](https://open.teambition.com/docs/apis/684a3a42912d20d3b5bcea9f) | **Get** /v3/projectplan/{projectPlanId}/members/list | 查询计划成员角色
*ProjectplanAPI* | [**ListPlanVersionsV3**](https://open.teambition.com/docs/apis/684a341d912d20d3b5aff931) | **Get** /v3/projectplan/{projectPlanId}/version/list | 查询计划版本列表
*ProjectplanAPI* | [**ListProjectPlanTasksLegacyV3**](https://open.teambition.com/docs/apis/682d4da6912d20d3b5bc4684) | **Get** /v3/projectplan-task/plans/{projectPlanId}/tasks | 获取计划任务列表
*ProjectplanAPI* | [**ListVisiblePlansV3**](https://open.teambition.com/docs/apis/682464b6912d20d3b5175b79) | **Get** /v3/projectplan/projects/{projectId}/list | 查询用户可见的计划列表
*ProjectplanAPI* | [**SearchProjectPlanTasksV3**](https://open.teambition.com/docs/apis/6822be41912d20d3b528f442) | **Get** /v3/project/{projectId}/plan-task/search | 通过TQL搜索项目计划任务
*ProjectplanAPI* | [**UpdatePlanApprovalV3**](https://open.teambition.com/docs/apis/67f36f5e8657139bff2be59c) | **Put** /v3/projectplan/plans/{projectPlanId}/approve | 更新计划审批信息
*ProjectplanAPI* | [**UpdatePlanCustomStatusV3**](https://open.teambition.com/docs/apis/67dd2d338657139bff29c843) | **Put** /v3/projectplan/plans/{projectPlanId}/customStatus | 配置计划自定义状态
*ProjectplanAPI* | [**UpdatePlanMemberRoleV3**](https://open.teambition.com/docs/apis/67e24a3e38cb5ab7af0b344c) | **Post** /v3/projectplan/plans/{projectPlanId}/members | 修改计划成员角色
*ProjectplanAPI* | [**UpdateProjectPlanTaskV3**](https://open.teambition.com/docs/apis/683570b6912d20d3b5f3e246) | **Put** /v3/projectplan-task/plans/{projectPlanId}/tasks/{taskId} | 更新计划任务（标题、开始时间、截止时间）
*ReportAPI* | [**SumProjectWorkTime**](https://open.teambition.com/docs/apis/63a4237d912d20d3b57fbd65) | **Post** /report/project/{projectId}/statistics/worktime/total | 计算项目总工时
*ReportAPI* | [**SumWorkTimeByUser**](https://open.teambition.com/docs/apis/63a4237d912d20d3b57fbbc4) | **Post** /report/project/{projectId}/statistics/worktime | 按人维度汇总工时
*SeatAPI* | [**CreateQuotaRule**](https://open.teambition.com/docs/apis/649aa48d11b042002ab6f10c) | **Post** /seat/project/allocate | 创建名额分配规则
*SfcAPI* | [**CreateSfcV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49c04) | **Post** /v3/sfc/create | 创建项目任务类型(提交项目ID), 创建企业任务类型
*SfcAPI* | [**DeleteSfcFieldV3**](https://open.teambition.com/docs/apis/63c7e586912d20d3b53ceb55) | **Post** /v3/sfc/{sfcId}/sf/delete | 删除项目/企业的任务类型的字段
*SfcAPI* | [**DeleteSfcV3**](https://open.teambition.com/docs/apis/63a08188912d20d3b56b90bb) | **Post** /v3/sfc/{sfcId}/delete | 删除项目任务类型(提交项目ID), 删除企业任务类型
*SfcAPI* | [**SearchOrgSfcV3**](https://open.teambition.com/docs/apis/63ee3ea2912d20d3b543f1ae) | **Get** /v3/scenariofieldconfig/search | 搜索企业任务类型
*SfcAPI* | [**UpdateSfcFieldV3**](https://open.teambition.com/docs/apis/63c7e586912d20d3b53cebc0) | **Post** /v3/sfc/{sfcId}/sf | 创建/修改 项目/企业的任务类型的字段
*SfcAPI* | [**UpdateSfcTaskflowV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49cf7) | **Put** /v3/sfc/{sfcId}/taskflow | 修改项目下任务类型绑定工作流
*SfcAPI* | [**UpdateSfcV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a49c43) | **Put** /v3/sfc/{sfcId} | 修改项目任务类型(提交项目ID), 修改企业任务类型
*TagAPI* | [**CreateOrgTagV3**](https://open.teambition.com/docs/apis/63ee3ea2912d20d3b543f21f) | **Post** /v3/tag/create | 创建企业标签
*TagAPI* | [**SearchOrgTagsV3**](https://open.teambition.com/docs/apis/63ee3ea2912d20d3b543f28b) | **Get** /v3/tag/search | 搜索企业标签
*TaskAPI* | [**ArchiveTaskV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a43a) | **Put** /v3/task/{taskId}/archive | 归档任务(移入回收站)
*TaskAPI* | [**CreateTaskCommentV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a469) | **Post** /v3/task/{taskId}/comment | 评论任务
*TaskAPI* | [**CreateTaskDependencyV3**](https://open.teambition.com/docs/apis/65bcb725912d20d3b57a1c76) | **Post** /v3/task/dependency/create | 创建任务依赖
*TaskAPI* | [**CreateTaskLinkV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a728) | **Post** /v3/task/{taskId}/objectlinks | 创建任务关联
*TaskAPI* | [**CreateTaskTraceV3**](https://open.teambition.com/docs/apis/63ee3ea3912d20d3b543f315) | **Post** /v3/task/{taskId}/trace/create | 创建任务进展
*TaskAPI* | [**CreateTaskV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a514) | **Post** /v3/task/create | 创建任务
*TaskAPI* | [**DeleteTaskDependencyV3**](https://open.teambition.com/docs/apis/65e5c202912d20d3b50a63ad) | **Post** /v3/task/dependency/{dependencyId}/delete | 删除任务依赖
*TaskAPI* | [**DeleteTaskLinkV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a754) | **Delete** /v3/task/{taskId}/objectlinks/{objectlinkId} | 删除任务关联
*TaskAPI* | [**DeleteTaskV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a5e1) | **Post** /v3/task/{taskId}/delete | 删除任务
*TaskAPI* | [**GetTaskDependenciesV3**](https://open.teambition.com/docs/apis/63613a18912d20d3b5296e6d) | **Get** /v3/task/dependency | 获取任务依赖
*TaskAPI* | [**GetTaskLinksV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a6fb) | **Get** /v3/task/{taskId}/objectlinks | 获取任务关联列表
*TaskAPI* | [**GetTaskTableCustomFieldV3**](https://open.teambition.com/docs/apis/682c19c9912d20d3b5a477bf) | **Get** /v3/task/{taskId}/customfield/table | 获取任务的表格自定义字段
*TaskAPI* | [**GetTaskTracesV3**](https://open.teambition.com/docs/apis/6363bcfa912d20d3b56faed0) | **Get** /v3/task/{taskId}/traces | 获取任务进展
*TaskAPI* | [**GetTemplateV2**](https://open.teambition.com/docs/apis/6321c6d4912d20d3b5a4b2e0) | **Get** /v2/template/info | 根据ID获取任务类型信息V2
*TaskAPI* | [**ListTaskActivitiesV3**](https://open.teambition.com/docs/apis/6363bcfb912d20d3b56fb3f4) | **Get** /v3/task/{taskId}/activity/list | 列出任务动态
*TaskAPI* | [**MoveOrgTaskToProject**](https://open.teambition.com/docs/apis/6823ee2e912d20d3b52ae3da) | **Post** /v3/organization-task/{taskId}/move | 轻任务移动到项目中
*TaskAPI* | [**MoveTaskV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a69f) | **Put** /v3/task/{taskId}/move | 跨项目移动任务
*TaskAPI* | [**QueryTaskV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a7b8) | **Get** /v3/task/query | 查询任务详情
*TaskAPI* | [**RenderTaskRtfV3**](https://open.teambition.com/docs/apis/65309201912d20d3b5cf2ab8) | **Get** /v3/task/rtf/render | 任务富文本内容渲染为 html
*TaskAPI* | [**RestoreTaskV3**](https://open.teambition.com/docs/apis/66601201912d20d3b584bcc8) | **Post** /v3/task/{taskId}/restore | 恢复任务(移出回收站)
*TaskAPI* | [**SearchTasksByTQL**](https://open.teambition.com/docs/apis/64264d3e912d20d3b5883b0e) | **Get** /all-task/search | 通过TQL搜索自由任务和项目任务ID
*TaskAPI* | [**SearchUserTasksV3**](https://open.teambition.com/docs/apis/63ee4160912d20d3b54548a6) | **Get** /v3/usertasks/search | 搜索用户的任务
*TaskAPI* | [**UpdateTaskContentV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a4a0) | **Put** /v3/task/{taskId}/content | 更新任务标题
*TaskAPI* | [**UpdateTaskCusomFieldByInstanceV3**](https://open.teambition.com/docs/apis/6321c6d1912d20d3b5a4a545) | **Post** /v3/task/{taskId}/customfield-instance/{instanceId}/update | 根据字段InstanceId更新任务自定义字段值(弃用)
*TaskAPI* | [**UpdateTaskCusomFieldV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a579) | **Post** /v3/task/{taskId}/customfield/update | 更新任务自定义字段值
*TaskAPI* | [**UpdateTaskCustomField**](https://open.teambition.com/docs/apis/6321c6d4912d20d3b5a4b391) | **Post** /task/customfield/update | 更新任务字段信息
*TaskAPI* | [**UpdateTaskCustomFieldV2**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a5a8) | **Post** /v3/task/{taskId}/customfield/{customfieldId}/update | 更新任务自定义字段值(弃用)
*TaskAPI* | [**UpdateTaskDueDateV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a613) | **Put** /v3/task/{taskId}/dueDate | 更新任务截止时间
*TaskAPI* | [**UpdateTaskExecutorV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a63d) | **Put** /v3/task/{taskId}/executor | 更新任务执行者
*TaskAPI* | [**UpdateTaskLockV3**](https://open.teambition.com/docs/apis/662213a0912d20d3b50bfd84) | **Post** /v3/task/{taskId}/access-policy/update | 更新任务加锁/解锁动作
*TaskAPI* | [**UpdateTaskMembersV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a66a) | **Put** /v3/task/{taskId}/involveMembers | 更新任务参与者
*TaskAPI* | [**UpdateTaskNoteV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a6ca) | **Put** /v3/task/{taskId}/note | 更新任务备注
*TaskAPI* | [**UpdateTaskParentV3**](https://open.teambition.com/docs/apis/63a0818a912d20d3b56b9dea) | **Put** /v3/task/{taskId}/parent | 改变任务的父任务
*TaskAPI* | [**UpdateTaskPriorityV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a780) | **Put** /v3/task/{taskId}/priority | 更新任务优先级
*TaskAPI* | [**UpdateTaskProgressV3**](https://open.teambition.com/docs/apis/63a0818a912d20d3b56b9d88) | **Put** /v3/task/{taskId}/progress | 更新任务进度
*TaskAPI* | [**UpdateTaskSfcV3**](https://open.teambition.com/docs/apis/64b0bc0f912d20d3b5178ce9) | **Put** /v3/task/{taskId}/sfc/update | 更新任务的任务类型
*TaskAPI* | [**UpdateTaskSprintV3**](https://open.teambition.com/docs/apis/63ab255a912d20d3b596c750) | **Put** /v3/task/{taskId}/sprint | 更新任务迭代
*TaskAPI* | [**UpdateTaskStageV3**](https://open.teambition.com/docs/apis/63a0818a912d20d3b56b9e50) | **Put** /v3/task/{taskId}/stage/update | 更新任务列表
*TaskAPI* | [**UpdateTaskStartDateV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a7ea) | **Put** /v3/task/{taskId}/startDate | 更新任务开始时间
*TaskAPI* | [**UpdateTaskStatusV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a844) | **Put** /v3/task/{taskId}/taskflowstatus | 更新任务状态
*TaskAPI* | [**UpdateTaskStoryPointV3**](https://open.teambition.com/docs/apis/63a0818a912d20d3b56b9efc) | **Put** /v3/task/{taskId}/storyPoint | 更新任务StoryPoint
*TaskAPI* | [**UpdateTaskTableCustomFieldV3**](https://open.teambition.com/docs/apis/682c19c9912d20d3b5a47827) | **Put** /v3/task/{taskId}/customfield/table | 更新任务的表格自定义字段
*TaskAPI* | [**UpdateTaskTagsV3**](https://open.teambition.com/docs/apis/6321c6d2912d20d3b5a4a819) | **Put** /v3/task/{taskId}/tag | 更新任务标签
*TaskAPI* | [**UpdateTaskVisibilityV3**](https://open.teambition.com/docs/apis/664c4d76912d20d3b50bde6e) | **Post** /v3/task/{taskId}/visible/update | 更新任务可见性
*TaskflowAPI* | [**SearchOrgTaskFlowsV3**](https://open.teambition.com/docs/apis/6593c8ee912d20d3b5cd6bc6) | **Get** /v3/taskflow/search | 搜索企业工作流
*TestcaseAPI* | [**CreateTestCaseV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c0c6) | **Post** /v3/project/{projectId}/testcase/create | 创建测试用例
*TestcaseAPI* | [**GetProjectTestHubV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c179) | **Get** /v3/project/{projectId}/testhub | 查询项目用例库
*TestcaseAPI* | [**PlanTestCaseV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c236) | **Post** /v3/project/{projectId}/testplan/{testplanId}/planning | 规划测试用例
*TestcaseAPI* | [**QueryOrgTestHubsV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c2fa) | **Get** /v3/testhub/query | 查询企业用例库列表
*TestcaseAPI* | [**QueryOrgUserCasesV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c355) | **Get** /v3/testhub/{testhubId}/usercase/query | 查询企业用例库用例列表V2
*TestcaseAPI* | [**QueryProjectTestHubCasesV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c1d3) | **Get** /v3/project/{projectId}/testhub/{testhubId}/usercase/query | 查询项目用例库用例列表
*TestcaseAPI* | [**QueryTestCasesV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c11e) | **Get** /v3/project/{projectId}/testcase/query | 查询测试用例列表
*TestcaseAPI* | [**QueryTestGroupsV3**](https://open.teambition.com/docs/apis/67bbec67912d20d3b55c8242) | **Post** /v3/group/query | 批量查询用例分组
*TestcaseAPI* | [**UpdateTestCaseFlowStatusV3**](https://open.teambition.com/docs/apis/67bbe1a8912d20d3b545c29a) | **Put** /v3/project/{projectId}/testplan/{testplanId}/testcase/{id}/flowStatusId | 更新测试用例状态
*WebhookAPI* | [**GetEgressIps**](https://open.teambition.com/docs/apis/63ec5732ccca5b002ad4052a) | **Get** /webhook/ips | 获取webhook出口IP列表
*WebhookAPI* | [**RestartWebhookListen**](https://open.teambition.com/docs/apis/65a0ba1865a529002b97eefa) | **Post** /webhook/v1/apps/{appId}/listen | 消费者服务启动并开始监听上报
*WorktimeAPI* | [**AggregateUserPlanTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a4901c) | **Post** /plantime/aggregation/datesUsers | 获取一定时间内订阅的指定用户的计划工时聚合数
*WorktimeAPI* | [**AggregateUserWorkTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a49110) | **Post** /worktime/aggregation/datesUsers | 获取一定时间内订阅的指定用户的实际工时聚合数据
*WorktimeAPI* | [**CreatePlanTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a48f2c) | **Post** /plantime/create | 创建计划工时
*WorktimeAPI* | [**CreateWorkTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a49058) | **Post** /worktime/create | 创建实际工时
*WorktimeAPI* | [**CreateWorkTimeApproval**](https://open.teambition.com/docs/apis/64337954e66e7e002b322169) | **Post** /worktime/approve/submit | 创建实际工时审批对象
*WorktimeAPI* | [**DeletePlanTime**](https://open.teambition.com/docs/apis/640d7cfa7b2cae002b71a567) | **Delete** /plantime/{plantimeId} | 删除计划工时单条记录
*WorktimeAPI* | [**DeleteWorkTime**](https://open.teambition.com/docs/apis/6405ce05b07df7002be7613d) | **Delete** /worktime/{worktimeId} | 删除实际工时单条记录
*WorktimeAPI* | [**GetPlanTimeDetail**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a48f72) | **Get** /plantime/{plantimeId} | 获取单个计划工时详情
*WorktimeAPI* | [**GetWorkTimeDetail**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a49082) | **Get** /worktime/{worktimeId} | 获取单个实际工时详情
*WorktimeAPI* | [**ListPlanTimes**](https://open.teambition.com/docs/apis/6376eefa912d20d3b59cde89) | **Get** /plantime/query | 获取用户所有计划工时详情数据
*WorktimeAPI* | [**ListTaskPlanTimes**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a48fa1) | **Get** /plantime/list/task/{taskId} | 获取单个任务的计划工时列表
*WorktimeAPI* | [**ListTaskWorkTimes**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a490b3) | **Get** /worktime/list/task/{taskId} | 获取单个任务的实际工时列表
*WorktimeAPI* | [**ListWorkTimes**](https://open.teambition.com/docs/apis/6376eefa912d20d3b59cdeee) | **Get** /worktime/query | 获取用户所有实际工时详情数据
*WorktimeAPI* | [**SumTaskPlanTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a48fd3) | **Get** /plantime/aggregation/task/{taskId} | 获取单个任务的计划工时总和
*WorktimeAPI* | [**SumTaskWorkTime**](https://open.teambition.com/docs/apis/6321c6cf912d20d3b5a490e1) | **Get** /worktime/aggregation/task/{taskId} | 获取单个任务的实际工时总和
*WorktimeAPI* | [**UpdatePlanTime**](https://open.teambition.com/docs/apis/640593c1bccdde0036d568f9) | **Put** /plantime/{plantimeId} | 更新计划工时单条记录
*WorktimeAPI* | [**UpdateWorkTime**](https://open.teambition.com/docs/apis/640594b7b07df7002be69f92) | **Put** /worktime/{worktimeId} | 更新实际工时单条记录
*WorktimeAPI* | [**UpdateWorkTimeApproval**](https://open.teambition.com/docs/apis/6433c0d2e66e7e002b32b7d3) | **Put** /worktime/approve/{openId} | 更新工时审批对象
*WorktimeAPI* | [**UpdateWorkTimeLimit**](https://open.teambition.com/docs/apis/66166278912d20d3b5b0af37) | **Put** /worktime/restriction | 更新工时企业人天的最大填报时间限制

