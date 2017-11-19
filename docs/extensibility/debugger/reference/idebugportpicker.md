---
title: "IDebugPortPicker |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee5b500f0ba42f7aa3b56439d34f88294b3b3717
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportpicker"></a>IDebugPortPicker
ポートを選択するためには、カスタマイズした UI を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、ポート サプライヤーによって実装されます。 ポートのサプライヤー CLSID として公開することをポイントして、ポートの選択を定義する、`metricPortPickerCLSID`で公開されている CLSID メトリック。  
  
## <a name="methods"></a>メソッド  
 次の表は、メソッドの`IDebugPortPicker`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|ユーザーがポートを選択できる指定されたダイアログ ボックスが表示されます。|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|サービス プロバイダーを設定します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll