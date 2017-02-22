---
title: "IDebugObject2::IsUserData | Microsoft Docs"
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
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData メソッド"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

オブジェクトはユーザー データを表すかどうかを判断します。  
  
## 構文  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### パラメーター  
 `pfUser`  
 \[入力\] オブジェクトはユーザー データを表す場合はを返します。`TRUE`\); ゼロ \(`FALSE`\)。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 ユーザー データはJustMyCode \(ユーザー コードとしてモジュールはスタック トレースに表示される示す指定したユーザー\) として設定できるオプションのオブジェクト モジュールの一部です。  
  
## 参照  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)