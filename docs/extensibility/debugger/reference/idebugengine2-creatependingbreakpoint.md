---
title: "IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
helpviewer_keywords: 
  - "IDebugEngine2::CreatePendingBreakpoint"
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジン \(DE\) の保留中のブレークポイントを作成します。  
  
## 構文  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```c#  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### パラメーター  
 `pBPRequest`  
 \[入力\] 作成する保留中のブレークポイントを表すオブジェクトの [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)。  
  
 `ppPendingBP`  
 \[入力\] 保留中のブレークポイントを表す [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  通常 `pBPRequest` のパラメーターが無効または不完全な場合は `pBPRequest` のパラメーターが DE のでサポートされる言語と一致する `E_FAIL` を返します。  
  
## 解説  
 保留中のブレークポイントは主にコードにブレークポイントをバインドするために必要なすべての情報のコレクションです。  このメソッドから返される保留中のブレークポイントはコードに [バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) のメソッドが呼び出されるまでバインドされません。  
  
 それぞれの保留中のブレークポイントに設定してデバッグ セッションごとにアタッチされた DE マネージャー \(SDM\) でこのメソッドを呼び出します。  これはブレークポイントがde\-DE 上で動作するプログラムに対して有効であることを確認するかどうかを決定します。  
  
 ユーザーがコード行にブレークポイントがde\-DE このコードに対応するドキュメントに最も近いシーケンス ポイントの行にブレークポイントのバインディングを自由になります。  これはすべてのコードはデバッグ情報で属性を使用する場合\) はユーザーが複数行ステートメントの最初の行にブレークポイントを設定したを最後の行のようにバインドする。  
  
## 使用例  
 次の例に `CProgram` の単純なオブジェクトに対してこのメソッドを実装する方法を示します。  DE の `IDebugEngine2::CreatePendingBreakpoint` の実装では各プログラムでこのメソッドの実装にすべての呼び出しを転送できます。  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)