---
title: IDebugPortPicker |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1b92f188dd2bed678e4117adde7c61d8844e8360
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545142"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugPortPicker](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportpicker)します。  
  
ポートを選択するためには、カスタマイズした UI を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 このインターフェイスは、ポートのサプライヤーによって実装されます。 ポート サプライヤー CLSID として公開し、ポイントし、ポートの選択を定義する、`metricPortPickerCLSID`で公開されている CLSID メトリック。  
  
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

