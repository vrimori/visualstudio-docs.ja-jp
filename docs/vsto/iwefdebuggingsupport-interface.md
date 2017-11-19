---
title: "IWefDebuggingSupport インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7768465f46e5344b88da9006a7de2396e3b75ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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
  
  