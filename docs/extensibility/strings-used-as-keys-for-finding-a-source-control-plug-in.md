---
title: "ソース管理プラグインを検索するためのキーとして使用される文字列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 1acc753d2a02c3be88687a4e42d71d23e988af48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>ソース管理プラグインを検索するためのキーとして使用される文字列
次の文字列は、詳細を確認するソース管理プラグインのレジストリにアクセスするためのキーです。  
  
 `STR_SCC_PROVIDER_REG_LOCATION`、 `STR_PROVIDERREGKEY`、 `STR_SCCPROVIDERPATH`、および`STR_SCCPROVIDERNAME`はレジストリ キーまたは値がソース管理プラグインとして Visual Studio の DLL を登録するために使用します。  
  
 `SCC_PROJECTNAME_KEY`、 `SCC_PROJECTAUX_KEY`、 `SCC_KEY, SCC_FILE_SIGNATURE`、および`SCC_STATUS_FILE`、MSSCCPRJ の形式を記述するために使用します。SCC ファイルです。  
  
## <a name="string-keys-and-values"></a>String キーと値  
  
|キー|[値]|  
|---------|-----------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|ソース コード管理|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|  
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ です。SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|コントロールのソース コード ファイル|  
|`SCC_NSE`|Namespace 拡張機能|  
|`SCC_NSE_PREFIX`|Protocal プレフィックス|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)