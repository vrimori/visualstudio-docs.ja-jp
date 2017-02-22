---
title: "ソース管理プラグインを検索するためのキーとして使用される文字列 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを検索に使用される文字列"
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# ソース管理プラグインを検索するためのキーとして使用される文字列
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

次の文字列とは、詳細を確認するソース管理プラグインのレジストリにアクセスするためのキーです。  
  
 `STR_SCC_PROVIDER_REG_LOCATION`, 、`STR_PROVIDERREGKEY`, 、`STR_SCCPROVIDERPATH`, 、および `STR_SCCPROVIDERNAME` レジストリ キーまたは値が、ソース管理プラグインとして Visual Studio の DLL を登録するために使用します。  
  
 `SCC_PROJECTNAME_KEY`, 、`SCC_PROJECTAUX_KEY`, 、`SCC_KEY, SCC_FILE_SIGNATURE`, 、および `SCC_STATUS_FILE` 、MSSCCPRJ の書式を記述するために使用します。SCC ファイルです。  
  
## 文字列キーと値  
  
|キー|値|  
|--------|-------|  
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\\SourceCodeControlProvider|  
|`STR_PROVIDERREGKEY`|ProviderRegKey|  
|`STR_SCCPROVIDERPATH`|SCCServerPath|  
|`STR_SCCPROVIDERNAME`|SCCServerName|  
|`STR_SCC_INI_SECTION`|ソース コード管理|  
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|  
|`SCC_PROJECTNAME_KEY`|SCC\_Project\_Name|  
|`SCC_PROJECTAUX_KEY`|SCC\_Aux\_Path|  
|`SCC_STATUS_FILE`|MSSCCPRJ します。ソース コード管理|  
|`SCC_KEY`|ソース コード管理|  
|`SCC_FILE_SIGNATURE`|コントロールのソース コード ファイル|  
|`SCC_NSE`|名前空間の拡張機能|  
|`SCC_NSE_PREFIX`|プロトコル プレフィックス|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\\Microsoft\\SourceSafe|  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [方法: ソース管理プラグインのインストール](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [MSSCCPRJ します。SCC ファイル](../extensibility/mssccprj-scc-file.md)