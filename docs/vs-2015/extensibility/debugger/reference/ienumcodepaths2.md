---
title: IEnumCodePaths2 |Microsoft Docs
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
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d24b05ee02eecf5e15eb61a80d25f00d1c46db4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246000"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)

