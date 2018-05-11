---
title: IWefDebuggingSupport インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e8a1bc770ce030902691a8ee4f2634c79cbab9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport インターフェイス
  Office 用アプリのデバッグを容易にするために、Visual Studio などのデバッグ環境によって実装されます。 Word や Excel など、Office アプリケーションでは、Visual Studio からこのインターフェイスを取得し、デバッグ セッション中に特定の時点で、インターフェイスのメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>メソッド  
 IWefDebuggingSupport インターフェイスを定義するメソッドを次の表に示します。  
  
|名前|説明|  
|----------|-----------------|  
|[GetAutoInsertExtensions メソッド](../vsto/getautoinsertextensions-method.md)|デバッグ中に自動的に挿入するのには、Office 用のアプリに関する情報を取得します。|  
|[SetWefProcessId メソッド](../vsto/setwefprocessid-method.md)|Web 拡張機能フレームワーク (WEF) のコンテンツを実行しているプロセス id を提供します。|  
  
  