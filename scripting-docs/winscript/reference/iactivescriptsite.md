---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite インターフェイス"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Windows のスクリプト エンジンのサイトを作成するには、ホストによって実装されます。  通常、このサイトは、スクリプト \(たとえば、ActiveX コントロール\) から参照できるすべてのオブジェクトのコンテナーに関連付けられます。  通常、このコンテナーに表示されるドキュメントまたはページに対応します。  Microsoft Internet Explorer は、たとえば、表示する各 HTML ページのこのようなコンテナーを作成します。  各ページの ActiveX コントロール \(またはそのほかのオートメーション オブジェクト\)、およびスクリプト エンジン自体は、このコンテナー内で列挙できます。  
  
## Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|ホストがユーザー インターフェイス要素を表示するために使用するロケール識別子を取得します。|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) メソッドの呼び出しによってエンジンに追加された項目に関する情報を取得します。|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|ホストから見た現在のドキュメントのバージョンを区別するホスト定義の文字列を取得します。|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|スクリプトが実行を完了したときに呼び出されます。|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|スクリプト エンジンの状態を変更したことをホストに通知します。|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|エンジンがスクリプトの実行中に実行エラーが発生したことをホストに通知します。|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|スクリプト エンジンがスクリプト コードの実行が開始されたことをホストに通知します。|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|スクリプト エンジンがスクリプト コードの実行が戻ったことをホストに通知します。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)