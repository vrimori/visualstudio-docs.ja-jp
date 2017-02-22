---
title: "BP_FLAGS | Microsoft Docs"
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
  - "BP_FLAGS"
helpviewer_keywords: 
  - "BP_FLAGS 列挙型"
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントを設定したときに追加情報を指定するために使用できるオプションのフラグを指定します。  
  
## 構文  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```c#  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## メンバー  
 BP\_FLAG\_NONE  
 ブレークポイントのフラグを指定しません。  
  
 BP\_FLAG\_MAP\_DOCPOSITION  
 デバッグ エンジンはドキュメントの場所 \(DE\) を使用してブレークポイントをマップする必要があることを指定します。  これはActive Server Pages\) などのスクリプト指向のソース ファイルにブレークポイントにのみ適用される設定です \(ASP\)。  
  
 BP\_FLAG\_DO のない \_STOP  
 デバッグ エンジンは最終的にはに停止する必要があります。ブレークポイントがデバッグ エンジンによって処理される \([IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) オブジェクトのイベントを送信しないことを指定します。  このフラグはトレース ポイントと基本的に使用するように設計されています。  
  
## 解説  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) と [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体のメンバー `dwFlags` に使用されます。  
  
 これらの値はビットごとの `OR` と組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)