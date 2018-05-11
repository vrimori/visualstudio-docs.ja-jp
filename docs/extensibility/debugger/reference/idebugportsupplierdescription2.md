---
title: IDebugPortSupplierDescription2 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierDescription2 interface
ms.assetid: dd19b9d6-0703-44b3-9498-cedffa0ce5b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c15facb38037272dcf2cef4f06d84d835b874012
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportsupplierdescription2"></a>IDebugPortSupplierDescription2
により、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]内のテキストを表示するための UI、**トランスポート情報**のセクションで、**プロセスにアタッチする** ダイアログ ボックス。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortSupplierDescription2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、ポート サプライヤーによって実装されます。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugPortSupplierDescription2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDescription](../../../extensibility/debugger/reference/idebugportsupplierdescription2-getdescription.md)|ポートのサプライヤーの説明と説明のメタデータを取得します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll