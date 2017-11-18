---
title: "IActiveScriptSite |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Windows スクリプト エンジンのサイトを作成するホストによって実装されます。 通常、このサイトはスクリプト (たとえば、ActiveX コントロール) に表示されているすべてのオブジェクトのコンテナーに関連付けられます。 通常、このコンテナーは、ドキュメントまたは表示されているページに対応します。 たとえば、Microsoft Internet Explorer は、このような HTML ページが表示されている各のコンテナーを作成です。 各 ActiveX コントロール (またはその他のオートメーション オブジェクト)、ページと、スクリプト エンジンで、それ自体ではこのコンテナー内で列挙可能ななります。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|ユーザー インターフェイス要素を表示するため、ホストを使用するロケール識別子を取得します。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|呼び出すことによって、エンジンに追加された項目に関する情報を取得、 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)メソッドです。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|ホストの視点から現在のドキュメントのバージョンを一意に識別するホスト定義の文字列を取得します。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|スクリプトの実行が完了したときに呼び出されます。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|スクリプト エンジンの状態が変更されたことをホストに通知します。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|エンジンが、スクリプトの実行中に実行エラーが発生したことをホストに通知します。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|スクリプト エンジンのスクリプト コードの実行が開始したことをホストに通知します。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|スクリプト コードを実行してから、スクリプト エンジンが返されたことをホストに通知します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)