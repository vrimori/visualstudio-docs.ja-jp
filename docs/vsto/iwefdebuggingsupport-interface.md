---
title: IWefDebuggingSupport インターフェイス
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 73aff964cfb66d33e308aef6448fc0f0b1b27c09
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901020"
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport インターフェイス
  Office 用アプリのデバッグを容易に、Visual Studio などのデバッグ環境で実装されます。 Word や Excel など、Office アプリケーションでは、Visual Studio からこのインターフェイスを取得し、デバッグ セッション中に特定の時点で、インターフェイスのメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```csharp 
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
|[GetAutoInsertExtensions メソッド](../vsto/getautoinsertextensions-method.md)|デバッグ中に自動的に挿入される Office 用アプリに関する情報を取得します。|  
|[SetWefProcessId メソッド](../vsto/setwefprocessid-method.md)|Web 拡張機能フレームワーク (WEF) コンテンツを実行しているプロセス id を提供します。|  
