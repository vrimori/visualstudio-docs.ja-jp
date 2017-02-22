---
title: "IDebugProgram2::EnumCodePaths | Microsoft Docs"
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
  - "IDebugProgram2::EnumCodePaths"
helpviewer_keywords: 
  - "IDebugProgram2::EnumCodePaths"
ms.assetid: fb100c3c-9c29-4d63-bd1f-a3e531cb395f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::EnumCodePaths
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ソース ファイル内の指定した位置のコード パスのリストを取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumCodePaths(   
   LPCOLESTR            pszHint,  
   IDebugCodeContext2*  pStart,  
   IDebugStackFrame2*   pFrame,  
   BOOL                 fSource,  
   IEnumCodePaths2**    ppEnum,  
   IDebugCodeContext2** ppSafety  
);  
```  
  
```c#  
int EnumCodePaths(   
   string                 pszHint,  
   IDebugCodeContext2     pStart,  
   IDebugStackFrame2      pFrame,  
   Int                    fSource,  
   out IEnumCodePaths2    ppEnum,  
   out IDebugCodeContext2 ppSafety  
);  
```  
  
#### パラメーター  
 `pszHint`  
 \[入力\]  **ソース**  のカーソルまたは IDE の ENT1ENT \[入力\] ビューの下の単語に一致します。  
  
 `pStart`  
 \[入力\] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) に現在のコンテキスト コード。  
  
 `pFrame`  
 \[入力\] [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) に現在のブレークポイントに関連付けられているスタック フレーム。  
  
 `fSource`  
 \[入力\]`TRUE`\(\) ENT0ENT \[入力\] ビューまたはゼロ \(`FALSE`\) ENT1ENT \[入力\] ビューの場合は。  
  
 `ppEnum`  
 \[入力\] [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md) のオブジェクトを含むコード パスのリストを返します。  
  
 `ppSafety`  
 \[入力\] 選択されたコード パスがスキップされた [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) にブレークポイントを追加コード コンテキストとして設定するために返します。  これはショートサーキットのブール式の場合はなどに発生します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 コード パスはプログラムの現在の実行ポイントに取得されたメソッドの名前を記述したり機能します。  コード パスの一覧は呼び出し履歴を表します。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)