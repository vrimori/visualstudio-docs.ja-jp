---
title: IActiveScriptSiteWindow |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a160b17f4a46237ab78b378664a046fe8a0e7d4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345722"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
このインターフェイスはホストと同じオブジェクトのユーザー インターフェイスをサポートする[IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)します。 実装しませんサーバーなどのユーザー インターフェイスをサポートしないホスト、`IActiveScriptSiteWindow`インターフェイス。 スクリプト エンジンが呼び出すことによってこのインターフェイスにアクセスする`QueryInterface`から`IActiveScriptSite`します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|スクリプト エンジンを表示する必要がある、ポップアップ ウィンドウの所有者として機能するウィンドウ ハンドルを取得します。|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|有効または無効のメイン ウィンドウと同様、モードレス ダイアログ ボックスにホストをによりします。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)