---
title: '方法: スクリプト ドキュメントを表示 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bfa273f98cebdf61f865e03a02c9b2d5f22bfa9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474730"
---
# <a name="how-to-view-script-documents"></a>方法 : スクリプト ドキュメントを表示する
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の以前のバージョンでは、サーバー側スクリプトによって生成されたクライアント側スクリプト ファイルは [スクリプト エクスプローラー] ウィンドウに表示されました。 [スクリプト エクスプローラー] ウィンドウは非表示のことが多く、クライアント側スクリプトが利用できるかどうかが常に明確とは限りませんでした。  
  
 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] では、サーバー側スクリプトによって生成されたクライアント側スクリプト ファイルは、既定で表示されるソリューション エクスプローラーに表示されます。 [スクリプト エクスプローラー] ウィンドウは削除されました。  
  
 クライアント側スクリプト ファイルは、デバッグ モードまたは中断モードのときにのみ表示されます。 表示される、**スクリプト ドキュメント**ノード。  
  
 サーバー側スクリプト ファイルは常に表示されます。 表示される、  **\<web サイトのパス名 >** ノード。 ノードの名前には、この例と似ています。 `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>サーバー側スクリプト ドキュメントを表示するには  
  
1.  **ソリューション エクスプ ローラー**を開き、  **\<web サイトのパス名 >** ノード。  
  
2.  表示するスクリプト ファイルをダブルクリックします。  
  
     サーバー側スクリプト ファイルがソース ウィンドウに表示されます。  
  
### <a name="to-view-a-client-side-script-document"></a>クライアント側スクリプト ドキュメントを表示するには  
  
1.  **ソリューション エクスプ ローラー**を開き、**スクリプト ドキュメント**ノード。  
  
2.  表示するスクリプト ファイルをダブルクリックします。  
  
     クライアント側スクリプト ファイルがソース ウィンドウに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)