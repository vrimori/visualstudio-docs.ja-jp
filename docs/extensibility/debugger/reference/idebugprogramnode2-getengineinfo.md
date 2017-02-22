---
title: "IDebugProgramNode2::GetEngineInfo | Microsoft Docs"
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
  - "IDebugProgramNode2::GetEngineInfo"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetEngineInfo"
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムを実行するデバッグ エンジン \(DE\) の名前と ID を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```c#  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### パラメーター  
 `pbstrEngine`  
 \[入力\] プログラム \(C\+\+ 仕様を実行する DE の名前を返します : これは呼び出し元がエンジンの名前の必要がない場合\) を示す null ポインターです。  
  
 `pguidEngine`  
 \[入力\] プログラム \(C\+\+ 仕様を実行する DE のグローバル一意識別子を返します : これは呼び出し元がエンジンの GUID する必要がないことを示す\) null ポインターです。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)