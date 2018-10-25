---
title: コードの列挙子をコマンド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0f3e2578a20319e88f048ed0c8ffded5589b286d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852016"
---
# <a name="command-code-enumerator"></a>コマンド コードの列挙子
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この列挙子は、オプションの使用、 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)と[SccPopulateList](../extensibility/sccpopulatelist-function.md)にオプションが指定されていることを示します。  
  
## <a name="syntax"></a>構文  
  
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
  
## <a name="members"></a>メンバー  
 SCC_COMMAND_GET  
 対応する、 [SccGet](../extensibility/sccget-function.md)します。  
  
 SCC_COMMAND_CHECKOUT  
 対応する、 [SccCheckout](../extensibility/scccheckout-function.md)します。  
  
 SCC_COMMAND_CHECKIN  
 対応する、 [SccCheckin](../extensibility/scccheckin-function.md)します。  
  
 SCC_COMMAND_UNCHECKOUT  
 対応する、 [SccUncheckout](../extensibility/sccuncheckout-function.md)します。  
  
 SCC_COMMAND_ADD  
 対応する、 [SccAdd](../extensibility/sccadd-function.md)します。  
  
 SCC_COMMAND_REMOVE  
 対応する、 [SccRemove](../extensibility/sccremove-function.md)します。  
  
 SCC_COMMAND_DIFF  
 対応する、 [SccDiff](../extensibility/sccdiff-function.md)します。  
  
 SCC_COMMAND_HISTORY  
 対応する、 [SccHistory](../extensibility/scchistory-function.md)します。  
  
 SCC_COMMAND_RENAME  
 対応する、 [SccRename](../extensibility/sccrename-function.md)します。  
  
 SCC_COMMAND_PROPERTIES  
 対応する、 [SccProperties](../extensibility/sccproperties-function.md)します。  
  
 SCC_COMMAND_OPTIONS  
 対応する、 [SccSetOption](../extensibility/sccsetoption-function.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)

