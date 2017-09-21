---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスの境界を越えて指定されたインターフェイスを取得します。  
  
## 構文  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### パラメーター  
 `riid`  
 \[入力\] 取得するインターフェイスの GUID。  
  
 `ppvObject`  
 \[入力\] 目的のインターフェイスを実装するオブジェクトを返します。  \[C\+\+\] これにより目的のインターフェイス型に直接キャストできます。  \[C\#\] 目的のインターフェイスを取得するに <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> のメソッドを使用します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはデバッグ エンジンは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] のプロセス空間で実行しデバッグするプログラムを独自のプロセス空間の実行中に使用されます。  
  
## 参照  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)