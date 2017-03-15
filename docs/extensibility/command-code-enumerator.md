---
title: "コマンドのコードの列挙子 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンドのコードの列挙子"
  - "ソース管理プラグインをコマンド コードの列挙"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# コマンドのコードの列挙子
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

オプションでこの列挙子が使用される、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) と [SccPopulateList](../extensibility/sccpopulatelist-function.md)するオプションが指定されていることを示します。  
  
## 構文  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## メンバー  
 SCC\_COMMAND\_GET  
 対応する、 [SccGet](../extensibility/sccget-function.md)です。  
  
 SCC\_COMMAND\_CHECKOUT  
 対応する、 [SccCheckout](../extensibility/scccheckout-function.md)です。  
  
 SCC\_COMMAND\_CHECKIN  
 対応する、 [SccCheckin](../extensibility/scccheckin-function.md)です。  
  
 SCC\_COMMAND\_UNCHECKOUT  
 対応する、 [SccUncheckout](../extensibility/sccuncheckout-function.md)です。  
  
 SCC\_COMMAND\_ADD  
 対応する、 [SccAdd](../extensibility/sccadd-function.md)です。  
  
 SCC\_COMMAND\_REMOVE  
 対応する、 [SccRemove](../extensibility/sccremove-function.md)です。  
  
 SCC\_COMMAND\_DIFF  
 対応する、 [SccDiff](../extensibility/sccdiff-function.md)です。  
  
 SCC\_COMMAND\_HISTORY  
 対応する、 [SccHistory](../extensibility/scchistory-function.md)です。  
  
 SCC\_COMMAND\_RENAME  
 対応する、 [SccRename](../extensibility/sccrename-function.md)です。  
  
 SCC\_COMMAND\_PROPERTIES  
 対応する、 [SccProperties](../extensibility/sccproperties-function.md)です。  
  
 SCC\_COMMAND\_OPTIONS  
 対応する、 [SccSetOption](../extensibility/sccsetoption-function.md)です。  
  
## 参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)