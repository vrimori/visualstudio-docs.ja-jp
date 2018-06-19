---
title: IDebugPortPicker |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7d9a5a830d6b3b0d191b5eae84bf625ffdb3b695
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118545"
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