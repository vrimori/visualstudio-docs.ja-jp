---
title: IActiveScriptAuthor インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptAuthor interface
ms.assetid: df1f454d-01ee-4beb-928b-48513d07365a
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9d9c2a330ee72c6a843cd42586a09bb1d51e3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346372"
---
# <a name="iactivescriptauthor-interface"></a>IActiveScriptAuthor インターフェイス
作成サービスは、IntelliSense や情報の照合順序を表します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptAuthor`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)|スクリプト エンジンの名前空間を作成するには、ルート レベルの項目の名前を追加します。 A*ルート レベルの項目*オブジェクト、プロパティとメソッドを含めることができ、イベント ソースを含むことができます。|  
|[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)|コード スクリプトレットをルート レベルの子として追加`IScriptNode`オブジェクト。 ホストでスクリプトレットの完全修飾名はのみに 2 つのレベルを持つことができます。|  
|[IActiveScriptAuthor::AddTypeLib](../../winscript/reference/iactivescriptauthor-addtypelib.md)|スクリプトの名前空間には、タイプ ライブラリを追加します。|  
|[IActiveScriptAuthor::GetChars](../../winscript/reference/iactivescriptauthor-getchars.md)|要求完了のコンテキストの終了文字のセットを返します。|  
|[IActiveScriptAuthor::GetEventHandler](../../winscript/reference/iactivescriptauthor-geteventhandler.md)|指定された属性を持つスクリプトレットを返します。|  
|[IActiveScriptAuthor::GetInfoFromContext](../../winscript/reference/iactivescriptauthor-getinfofromcontext.md)|返しますでは、コードのブロックの情報と、指定された文字のアンカー位置を入力します。 これにより、IntelliSense、グローバル リスト、およびパラメーターのヒント、メンバーの情報を提供します。|  
|[IActiveScriptAuthor::GetLanguageFlags](../../winscript/reference/iactivescriptauthor-getlanguageflags.md)|言語情報を返します。|  
|[IActiveScriptAuthor::GetRoot](../../winscript/reference/iactivescriptauthor-getroot.md)|返します、`IScriptNode`作成者のスクリプトのツリーのルート。|  
|[IActiveScriptAuthor::GetScriptletTextAttributes](../../winscript/reference/iactivescriptauthor-getscriptlettextattributes.md)|スクリプトレットのテキスト属性を返します。|  
|[IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)|スクリプト ブロックのテキスト属性を返します。|  
|[IActiveScriptAuthor::IsCommitChar](../../winscript/reference/iactivescriptauthor-iscommitchar.md)|指定された文字が、アプリケーションによってステートメント入力候補をコミットする必要があるかどうかを示す値を返します。|  
|[IActiveScriptAuthor::ParseScriptText](../../winscript/reference/iactivescriptauthor-parsescripttext.md)|スクリプト テキストを解析、オーサリングのスクリプト エンジンを作成するテキストを追加し、作成、`IScriptEntry`スクリプト ブロックに対応するオブジェクト。|  
|[IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)|削除、`NamedItem`エンジンを作成するスクリプトの名前空間のオブジェクト。|  
|[IActiveScriptAuthor::RemoveTypeLib](../../winscript/reference/iactivescriptauthor-removetypelib.md)|エンジンの名前空間を作成するスクリプトからタイプ ライブラリを削除します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト作成インターフェイス](../../winscript/reference/active-script-authoring-interfaces.md)