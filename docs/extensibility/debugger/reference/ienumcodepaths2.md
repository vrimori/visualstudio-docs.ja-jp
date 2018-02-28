---
title: "IEnumCodePaths2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f3da3fbbc8b7ad7dced8a9767b26859cc1a0de1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)