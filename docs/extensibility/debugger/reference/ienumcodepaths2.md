---
title: IEnumCodePaths2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20bfd418da802e136fd92948285f9431efae88ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982118"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
このインターフェイスは、コード パスの一覧を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、コード パスの一覧を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumCodePaths2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|指定された数の列挙体シーケンス内のコード パスを取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|指定された数の列挙体シーケンス内のコード パスをスキップします。|  
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|先頭に、列挙体シーケンスをリセットします。|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|現在の列挙子と同じ列挙状態を格納する列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|列挙子のコード パスの数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 コード パスでは、プログラムでは分岐ポイントまたは関数呼び出しを表します。 コード パスの一覧は、使用される、コードの実行が使用されるパスを表します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)