---
title: "SccUninitialize 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccUninitialize"
helpviewer_keywords: 
  - "SccUninitialize 関数"
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# SccUninitialize 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、すべての割り当てと開いている接続を以前の呼び出しによって作成されたクリーンアップ、 [SccInitialize](../extensibility/sccinitialize-function.md) 、ソース管理プラグインをシャット ダウンに備える。  
  
## 構文  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]作成したソース コントロールのプラグインの context 構造体へのポインター、 [SccInitialize](../extensibility/sccinitialize-function.md)です。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|クリーンアップを正常に完了しました。|  
  
## 解説  
 ソース管理プラグインでは、シャット ダウンするための準備と構造体のプラグインが割り当てたメモリを解放する責任者です。 関数は、プラグインの特定のインスタンスごとに 1 回呼び出されます。 呼び出し、 [SccInitialize](../extensibility/sccinitialize-function.md) この呼び出しの前にします。 プロジェクトを開いたままになっていないへの呼び出し時に `SccUninitialize`します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)