---
lang: en
lang-ref: actions
title: Actions
---

Each Actions are processed in Kernel/Modules/\*.pm files accordingly its names.

## Action Module Structure

Action module must have Run method which is run from

Kernel/System/Web/Interface(Agent\|Customer\|Public\|Installer).pm files.

## Action Module Testing

Tests for Actions modules are kept in scripts/test/Selenium/ directory.

- scripts/test/Selenium/Agent/Admin/ -- for Admin module .pm files
- scripts/test/Selenium/Agent/ -- for Agent module .pm files
- scripts/test/Selenium/Customer/ -- for Customer module .pm files

How to run it see [here](/en/testing/unit-tests)

## Action List

### Admin Actions

- AdminACL.pm
- AdminAppointmentCalendarManage.pm
- AdminAppointmentImport.pm
- AdminAppointmentNotificationEvent.pm
- AdminAttachment.pm
- AdminAutoResponse.pm
- AdminCloudServices.pm
- AdminCloudServiceSupportDataCollector.pm
- AdminCommunicationLog.pm
- AdminCustomerCompany.pm
- AdminCustomerGroup.pm
- AdminCustomerUserCustomer.pm
- AdminCustomerUserGroup.pm
- AdminCustomerUser.pm
- AdminCustomerUserService.pm
- AdminDynamicFieldCheckbox.pm
- AdminDynamicFieldDateTime.pm
- AdminDynamicFieldDropdown.pm
- AdminDynamicFieldMultiselect.pm
- AdminDynamicField.pm
- AdminDynamicFieldText.pm
- AdminEmail.pm
- AdminGenericAgent.pm
- AdminGenericInterfaceDebugger.pm
- AdminGenericInterfaceErrorHandlingDefault.pm
- AdminGenericInterfaceErrorHandlingRequestRetry.pm
- AdminGenericInterfaceInvokerDefault.pm
- AdminGenericInterfaceInvokerEvent.pm
- AdminGenericInterfaceMappingSimple.pm
- AdminGenericInterfaceMappingXSLT.pm
- AdminGenericInterfaceOperationDefault.pm
- AdminGenericInterfaceTransportHTTPREST.pm
- AdminGenericInterfaceTransportHTTPSOAP.pm
- AdminGenericInterfaceWebserviceHistory.pm
- AdminGenericInterfaceWebservice.pm
- AdminGroup.pm
- AdminInit.pm
- AdminLog.pm
- AdminMailAccount.pm
- AdminNotificationEvent.pm
- AdminOTRSBusiness.pm
- AdminPackageManager.pm
- AdminPerformanceLog.pm
- AdminPGP.pm
- Admin.pm
- AdminPostMasterFilter.pm
- AdminPriority.pm
- AdminProcessManagementActivityDialog.pm
- AdminProcessManagementActivity.pm
- AdminProcessManagementPath.pm
- AdminProcessManagement.pm
- AdminProcessManagementTransitionAction.pm
- AdminProcessManagementTransition.pm
- AdminQueueAutoResponse.pm
- AdminQueue.pm
- AdminQueueTemplates.pm
- AdminRegistration.pm
- AdminRoleGroup.pm
- AdminRole.pm
- AdminRoleUser.pm
- AdminSalutation.pm
- AdminSelectBox.pm
- AdminService.pm
- AdminSession.pm
- AdminSignature.pm
- AdminSLA.pm
- AdminSMIME.pm
- AdminState.pm
- AdminSupportDataCollector.pm
- AdminSystemAddress.pm
- AdminSystemConfigurationDeployment.pm
- AdminSystemConfigurationGroup.pm
- AdminSystemConfiguration.pm
- AdminSystemMaintenance.pm
- AdminTemplateAttachment.pm
- AdminTemplate.pm
- AdminType.pm
- AdminUserGroup.pm
- AdminUser.pm

### Agent Actions

- AgentAppointmentAgendaOverview.pm
- AgentAppointmentCalendarOverview.pm
- AgentAppointmentEdit.pm
- AgentAppointmentList.pm
- AgentAppointmentPluginSearch.pm
- AgentCustomerInformationCenter.pm
- AgentCustomerInformationCenterSearch.pm
- AgentCustomerSearch.pm
- AgentCustomerUserAddressBook.pm
- AgentCustomerUserInformationCenter.pm
- AgentCustomerUserInformationCenterSearch.pm
- AgentDaemonInfo.pm
- AgentDashboardCommon.pm
- AgentDashboard.pm
- AgentInfo.pm
- AgentLinkObject.pm
- AgentOTRSBusiness.pm
- AgentPreferences.pm
- AgentSearch.pm
- AgentSplitSelection.pm
- AgentStatistics.pm
- AgentTicketActionCommon.pm
- AgentTicketArticleContent.pm
- AgentTicketAttachment.pm
- AgentTicketBounce.pm
- AgentTicketBulk.pm
- AgentTicketClose.pm
- AgentTicketCompose.pm
- AgentTicketCustomer.pm
- AgentTicketEmailOutbound.pm
- AgentTicketEmail.pm
- AgentTicketEmailResend.pm
- AgentTicketEscalationView.pm
- AgentTicketForward.pm
- AgentTicketFreeText.pm
- AgentTicketHistory.pm
- AgentTicketLockedView.pm
- AgentTicketLock.pm
- AgentTicketMerge.pm
- AgentTicketMove.pm
- AgentTicketNote.pm
- AgentTicketOwner.pm
- AgentTicketPending.pm
- AgentTicketPhoneCommon.pm
- AgentTicketPhoneInbound.pm
- AgentTicketPhoneOutbound.pm
- AgentTicketPhone.pm
- AgentTicketPlain.pm
- AgentTicketPrint.pm
- AgentTicketPriority.pm
- AgentTicketProcess.pm
- AgentTicketQueue.pm
- AgentTicketResponsible.pm
- AgentTicketResponsibleView.pm
- AgentTicketSearch.pm
- AgentTicketService.pm
- AgentTicketStatusView.pm
- AgentTicketWatcher.pm
- AgentTicketWatchView.pm
- AgentTicketZoom.pm
- AgentUserSearch.pm
- AgentZoom.pm

### Customer Actions

- CustomerAccept.pm
- CustomerPreferences.pm
- CustomerTicketArticleContent.pm
- CustomerTicketAttachment.pm
- CustomerTicketMessage.pm
- CustomerTicketOverview.pm
- CustomerTicketPrint.pm
- CustomerTicketProcess.pm
- CustomerTicketSearch.pm
- CustomerTicketZoom.pm

### Public Actions

- PublicCalendar.pm
- PublicDefault.pm
- PublicRepository.pm
- PublicSupportDataCollector.pm

### Internal Actions

- AjaxAttachment.pm
- Installer.pm
- PictureUpload.pm
- Test.pm
