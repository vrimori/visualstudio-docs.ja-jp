---
title: "IEnumDebugReferenceInfo2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugReferenceInfo2
helpviewer_keywords: IEnumDebugReferenceInfo2
ms.assetid: 7ed01441-686f-4032-8268-a4c750f19f85
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9c7bcba4207e5caa14b9db27f2d9b243376c6d01
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugreferenceinfo2"></a>IEnumDebugReferenceInfo2
このインターフェイスの列挙[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDebugReferenceInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、メモリ内のオブジェクトへの参照のサポートの一部としてこのインターフェイスを実装します。 参照はサポートされている場合にのみ、このインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 Visual Studio 呼び出し[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugReferenceInfo2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-next.md)|指定した数を取得[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列挙のシーケンス内の構造体。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-skip.md)|指定した数のスキップ[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)列挙のシーケンス内の構造体。|  
|[リセット](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2-getcount.md)|数を取得[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体、列挙子にします。|  
  
## <a name="remarks"></a>コメント  
 参照は、プロパティは、名前、種類、およびアドレスは実質的に型と、アドレスです。 メモリ内に存在する、オブジェクトが参照されている限り、参照が保持されます。 参照してください[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)詳細についてはします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)