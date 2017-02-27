---
title: "SccCloseProject 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCloseProject"
helpviewer_keywords: 
  - "SccCloseProject 関数"
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# SccCloseProject 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、特定のセッションの終了位置を示す、プロジェクトを閉じます。  
  
## 構文  
  
```cpp#  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
#### パラメーター  
 pvContext  
 ソース管理プラグイン コンテキスト構造体。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|プロジェクトは正常に終了します。|  
|SCC\_E\_PROJNOTOPEN|プロジェクトは、現在開いているではありません。|  
|SCC\_E\_NOTAUTHORIZED|この操作を実行できません。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。|  
  
## 解説  
 [SccOpenProject](../extensibility/sccopenproject-function.md) は、この関数の前に必ず呼び出されます。 この関数に対する呼び出しはいずれかを呼び出した後、 `SccOpenProject` 関数または [SccUninitialize](../extensibility/sccuninitialize-function.md), 、ソース管理システムへの接続を完全に終了します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)