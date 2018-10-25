---
title: BP_FLAGS |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_FLAGS
helpviewer_keywords:
- BP_FLAGS enumeration
ms.assetid: c45dfc74-5e7f-4f1e-a147-ab2a55dccbd0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a819c822a813cd75ec72ff0883d36f19306d3d72
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829951"
---
# <a name="bpflags"></a>BP_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ブレークポイントを設定するときに、追加情報を指定するために使用するオプションのフラグを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
typedef DWORD BP_FLAGS;  
```  
  
```csharp  
public enum enum_BP_FLAGS {   
   BP_FLAG_NONE            = 0x0000,  
   BP_FLAG_MAP_DOCPOSITION = 0x0001,  
   BP_FLAG_DONT_STOP       = 0x0002  
};  
```  
  
## <a name="members"></a>メンバー  
 BP_FLAG_NONE  
 ブレークポイントのフラグを指定しません。  
  
 BP_FLAG_MAP_DOCPOSITION  
 デバッグ エンジン (DE) がドキュメントの位置を使用してブレークポイントをマップする必要がありますを指定します。 これは、機能は、Active Server Pages (ASP) などのスクリプトを使用したソース ファイルに設定されたブレークポイントにのみ適用されます。  
  
 BP_FLAG_DONT_STOP  
 デバッグ エンジン最終的に停止するようにされませんが、ブレークポイントが、デバッグ エンジンによって処理されることを指定 (つまり、 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)イベント オブジェクトを送信しない必要があります)。 このフラグは、トレース ポイントで主に使用する設計されています。  
  
## <a name="remarks"></a>Remarks  
 使用、`dwFlags`のメンバー、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)

