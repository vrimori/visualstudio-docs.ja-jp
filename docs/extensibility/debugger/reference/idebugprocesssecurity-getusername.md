---
title: "IDebugProcessSecurity::GetUserName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::GetUserName"
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ポートのサプライヤーからユーザー名を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```c#  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### パラメーター  
 `pbstrUserName`  
 \[入力\] 文字列ユーザー名。  
  
## 戻り値  
 メソッドが成功した場合は`S_OK` を返します。  それ以外の場合はエラー コードを返します。  
  
## 解説  
 `GetUserName` は ENT1ENT \[出力\] ダイアログ ボックスの \[出力\] 列に表示 ENT0ENT のユーザー名を返します。  \[ENT0ENT\] ダイアログ ボックスを表示するには[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の統合開発環境 \(ENT3ENT \[入力\] メニューの \[ENT1ENT\] を \(IDE\) クリックします。  
  
## 参照  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)