---
title: IEnumCodePaths2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fc2441d2257c5e3c3e6d205ea27b64e03938490b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120742"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
このインターフェイスは、コード パスの一覧を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、コード パスの一覧を表すためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)このインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IEnumCodePaths2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[次へ](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|列挙のシーケンス内のコード パスの指定した数を取得します。|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|列挙のシーケンス内のコード パスの指定した数をスキップします。|  
|[リセット](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|列挙のシーケンスを先頭にリセットします。|  
|[複製](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|現在の列挙子と同じ列挙の状態を含む列挙子を作成します。|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|列挙子内のコード パスの数を取得します。|  
  
## <a name="remarks"></a>コメント  
 コード パスでは、プログラムでの分岐ポイントまたは関数の呼び出しを表します。 コード パスの一覧では、使用する、コードの実行に使用されるパスを表します。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)