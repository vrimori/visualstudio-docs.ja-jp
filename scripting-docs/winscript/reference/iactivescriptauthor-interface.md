---
title: "IActiveScriptAuthor インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37abb356ab24d64a05a1f1209809d63e2f55e228
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor インターフェイス
IntelliSense および情報の照合順序など、サービスの作成を表します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptAuthor`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|スクリプト エンジンの名前空間を作成するには、ルート レベルの項目の名前を追加します。 A*ルート レベルの項目*プロパティとメソッドを持つことができるし、イベント ソースを持つことができるオブジェクトです。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|コード スクリプトレットをルート レベルの子として追加`IScriptNode`オブジェクト。 ホスト、スクリプトレットの完全修飾名には 2 つのレベルことができます。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|スクリプトの名前空間をタイプ ライブラリを追加します。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|要求完了コンテキストの終了文字のセットを返します。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|指定された属性を持つスクリプトレットを返します。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|情報と、指定された文字のアンカー位置は、コードのブロックの型を返します。 IntelliSense、グローバル リスト、およびパラメーターのヒントのメンバーについて情報を提供します。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|言語情報を返します。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|返します、`IScriptNode`作成者のスクリプトのツリーのルートです。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|スクリプトレットのテキスト属性を返します。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|スクリプト ブロックのテキスト属性を返します。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|指定された文字が、アプリケーションによってステートメント入力候補をコミットする必要があるかどうかを示す値を返します。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|スクリプトのテキストを解析して、エンジンをオーサリング オーサリング スクリプトに、テキストを追加し、作成、`IScriptEntry`スクリプト ブロックに対応するオブジェクト。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|削除、`NamedItem`エンジンを作成するスクリプトの名前空間のオブジェクト。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|エンジンの名前空間を作成、スクリプトからタイプ ライブラリを削除します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)