---
title: "IActiveScriptSiteWindow |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
同じオブジェクトのユーザー インターフェイスをサポートするホストによってこのインターフェイスは実装[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)です。 ホスト サーバーなどのユーザー インターフェイスをサポートしていない実装しない、`IActiveScriptSiteWindow`インターフェイスです。 スクリプト エンジンを呼び出してこのインターフェイスにアクセスする`QueryInterface`から`IActiveScriptSite`です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|スクリプト エンジンを表示する必要がありますがポップアップ ウィンドウの所有者として機能するウィンドウ ハンドルを取得します。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|で有効にするにまたはメイン ウィンドウと同様、モードレス ダイアログ ボックスを無効にするホスト。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)