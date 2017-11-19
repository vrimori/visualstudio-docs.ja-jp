---
title: "BP_FLAGS90 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: BP_FLAGS90 enumeration
ms.assetid: 3e5a06c5-fb30-4b8a-b2d5-4a0570fc80bd
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dddedfcbfe48f6ef6ceaedcdcfb1d7089307bcd3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="bpflags90"></a>BP_FLAGS90
省略可能なフラグの有効な値を列挙します。 省略可能なフラグは、ブレークポイントを設定すると、追加情報を指定するために可能性があります。 この列挙体を拡張、 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE               = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION    = 0x0001,  
   BP90_FLAG_DONT_STOP          = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
typedef DWORD BP_FLAGS90;  
```  
  
```csharp  
public enum enum_BP_FLAGS90  
{  
   // VS 8.0 values  
   BP90_FLAG_NONE                = 0x0000,  
   BP90_FLAG_MAP_DOCPOSITION     = 0x0001,  
   BP90_FLAG_DONT_STOP           = 0x0002,  
  
   // Values added in VS 9.0  
   BP90_FLAG_TRACEPOINT_CONTINUE = 0x0004,  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 BP90_FLAG_NONE  
 ブレークポイントのフラグを指定しません。  
  
 BP90_FLAG_MAP_DOCPOSITION  
 デバッグ エンジン (DE) がドキュメントの位置を使用して、ブレークポイントをマップする必要がありますを指定します。 これは、Active Server Pages (ASP) などのスクリプト指向のソース ファイルに設定されたブレークポイントにのみ適用されます。  
  
 BP90_FLAG_DONT_STOP  
 指定する、ブレークポイントがデバッグ エンジンによって処理されることは、デバッグ エンジンは、最終的をいない停止することがあります。つまり、 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)イベント オブジェクトを送信できません。 このフラグは、トレース ポイントで、主に使用するよう設計されています。  
  
 BP90_FLAG_TRACEPOINT_CONTINUE  
 ネイティブ デバッグ エンジンによってステップ実行の状態を消去する必要があるかどうかを決定するために使用します。 トレース ポイントは、マクロを実行する場合、BP90_FLAG_DONT_STOP が設定されていないため BP90_FLAG_DONT_STOP とは異なります。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)