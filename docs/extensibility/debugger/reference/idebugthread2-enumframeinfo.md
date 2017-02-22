---
title: "IDebugThread2::EnumFrameInfo | Microsoft Docs"
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
  - "IDebugThread2::EnumFrameInfo"
helpviewer_keywords: 
  - "IDebugThread2::EnumFrameInfo"
ms.assetid: 17914a71-10ea-4b6f-8982-e364f87dca53
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::EnumFrameInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このスレッドのスタック フレームの一覧を取得します。  
  
## 構文  
  
```cpp#  
HRESULT EnumFrameInfo (   
   FRAMEINFO_FLAGS        dwFieldSpec,  
   UINT                   nRadix,  
   IEnumDebugFrameInfo2** ppEnum  
);  
```  
  
```c#  
int EnumFrameInfo (   
   enum_FRAMEINFO_FLAGS     dwFieldSpec,  
   uint                     nRadix,  
   out IEnumDebugFrameInfo2 ppEnum  
);  
```  
  
#### パラメーター  
 `dwFieldSpec`  
 \[入力\] [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体のフィールドが設定方法を指定する [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) の列挙体のフラグの組み合わせ。  一つの文字列に関数名を書式設定する `FIF_FUNCNAME_FORMAT` フラグを指定します。  
  
 `nRadix`  
 \[入力\] 列挙子の数値情報の書式設定に使用された基数。  
  
 `ppEnum`  
 \[出力\] スタック フレームを示す [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造体のリストを含む [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 スレッドのフレームは最初に列挙されている現在のフレームと最後に列挙されて最も古いフレームの順序で列挙されます。  
  
## 参照  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [FRAMEINFO\_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)