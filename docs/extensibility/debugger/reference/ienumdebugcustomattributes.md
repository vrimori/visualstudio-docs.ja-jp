---
title: IEnumDebugCustomAttributes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebf7250f0845eb666b910b5ddcce266be1ea9361
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990647"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
カスタム属性を列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、カスタム属性をサポートするには、このインターフェイスを実装 (を通じて、 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)インターフェイス)。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)このインターフェイスを返します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumDebugCustomAttributes`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|指定された数の列挙体シーケンス内のカスタム属性を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|指定された数の列挙体シーケンス内のカスタム属性をスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|列挙子では、カスタム属性の数を取得します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)