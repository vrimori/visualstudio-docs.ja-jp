---
title: "IDispError インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispError インターフェイス"
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError インターフェイス
高度なコンテキスト詳細なエラー情報を収集します。  
  
> [!NOTE]
>  このインターフェイスは実行されません。  
  
 `IUnknown` から継承するメソッドに加え、`IDispError` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|エラー特定の種類の情報を取得します。|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|`IDispError` で次のオブジェクトを取得します。|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|`IDispError` のオブジェクトからエラー コードを取得します。|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|エラーを発生させたアプリケーションまたはクラスの言語に依存したプログラム ID を返します。|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|エラーを説明するトピックのファイルとヘルプ コンテキスト ID のパスを、可能であれば返します。|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|エラーのテキスト説明を返します。|