---
title: IDebugProperty3 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ae93a9f88bdee3c4648f803eaf174567fe771c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122783"
---
# <a name="idebugproperty3"></a>IDebugProperty3
このインターフェイスは、サポートを提供します。  
  
-   プロパティに関連付けられている任意の長さの文字列を取得しています。  
  
-   プロパティを使用して一意の ID を関連付けることです。  
  
-   プロパティのカスタム ビューアーの一覧を取得しています。  
  
-   生成されるエラーを報告する機能をプロパティの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) を実装する同一のオブジェクトにこのインターフェイスを実装する[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)長い文字列、プロパティ Id、およびカスタム ビューアーのサポートを提供します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、`IDebugProperty2`インターフェイスをこのインターフェイスを取得します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 継承されたメソッドだけでなく`IDebugProperty2`、`IDebugProperty3`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|プロパティに関連付けられている文字列の長さを返します。|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|ユーザーが指定したバッファー内の文字列を返します。|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|このプロパティの一意の ID を作成します。|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|このプロパティの一意の ID を破棄します。|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|カスタム ビューアーで表示できます。 このプロパティの数を返します。|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|カスタム ビューアーで表示できます。 このプロパティの一覧を返します。|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|何も問題が発生した場合は、エラー メッセージを返す、このプロパティの値を設定します。|  
  
## <a name="remarks"></a>コメント  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)はセッション デバッグ マネージャー (SDM) プロパティの値を設定することをお勧めします。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)