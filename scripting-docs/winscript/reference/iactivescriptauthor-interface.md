---
title: "IActiveScriptAuthor インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptAuthor インターフェイス"
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor インターフェイス
情報の IntelliSense と照合順序を含むサービスを作成、Represents。  
  
 `IUnknown` から継承するメソッドに加え、`IActiveScriptAuthor` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|エンジンの名前空間を作成スクリプトにルート レベルの名前を追加します。  *ルート レベルの項目は*、プロパティおよびメソッドを含めることもイベント ソースを含むオブジェクトです。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|ルート レベルの `IScriptNode` オブジェクトの子としてスクリプトレット コードを追加します。  ホストでは、スクリプトレットの完全限定名は 2 レベルだけを指定できます。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|スクリプトの名前空間にタイプ ライブラリを追加します。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|要求された実行コンテキストの終了文字のセットを返します。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|指定した属性を持つスクリプトレットを返します。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|戻り値は情報を入力し、コード ブロックの特定の文字の位置を固定します。  これは、メンバーの IntelliSense、グローバル リスト、およびパラメーターのヒントについて説明します。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|言語の情報を返します。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|作成者のスクリプトのツリーのルート `IScriptNode` を返します。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|スクリプトレットのテキスト属性を返します。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|スクリプト ブロックのテキスト属性を返します。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|特定の文字は、アプリケーションによってステートメントの完了をコミットするかどうかを示す値を返します。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|分析はテキストのスクリプトを作成したり、作成スクリプト エンジンの作成にテキストを追加し、スクリプト ブロックに対応する `IScriptEntry` のオブジェクトを作成します。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|エンジンの作成スクリプトの名前空間から `NamedItem` のオブジェクトを削除します。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|エンジンの名前空間を作成スクリプトからタイプ ライブラリを削除します。|  
  
## 参照  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)