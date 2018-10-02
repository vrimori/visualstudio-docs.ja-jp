---
title: ソース管理プラグインを検索するためのキーとして使用される文字列 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e2a663f11834a063faa0017cd37f6f542ab98ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538751"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>ソース管理プラグインを検索するためのキーとして使用される文字列
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[文字列は、ソース管理プラグインを検索するためのキーとして使用](https://docs.microsoft.com/visualstudio/extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in)します。  
  
次の文字列は、詳細を確認するソース管理プラグイン レジストリにアクセスするためのキーです。  
  
 `STR_SCC_PROVIDER_REG_LOCATION`、 `STR_PROVIDERREGKEY`、 `STR_SCCPROVIDERPATH`、および`STR_SCCPROVIDERNAME`レジストリ キーまたは値が、ソース管理プラグインとして for Visual Studio DLL を登録するために使用されます。  
  
 `SCC_PROJECTNAME_KEY`、 `SCC_PROJECTAUX_KEY`、 `SCC_KEY, SCC_FILE_SIGNATURE`、および`SCC_STATUS_FILE`、MSSCCPRJ の形式を記述するために使用します。SCC ファイルです。  
  
## <a name="string-keys-and-values"></a>文字列キーと値  
  
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
|`SCC_STATUS_FILE`|MSSCCPRJ します。SCC|  
|`SCC_KEY`|SCC|  
|`SCC_FILE_SIGNATURE`|コントロールのソース コード ファイル|  
|`SCC_NSE`|Namespace の拡張機能|  
|`SCC_NSE_PREFIX`|Protocal プレフィックス|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)

