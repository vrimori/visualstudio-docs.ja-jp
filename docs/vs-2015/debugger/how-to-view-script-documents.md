---
title: '方法: スクリプト ドキュメントを表示 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7f32fc5537fae9483401ac479eb4585d1e19108
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230514"
---
# <a name="how-to-view-script-documents"></a>方法 : スクリプト ドキュメントを表示する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の以前のバージョンでは、サーバー側スクリプトによって生成されたクライアント側スクリプト ファイルは [スクリプト エクスプローラー] ウィンドウに表示されました。 [スクリプト エクスプローラー] ウィンドウは非表示のことが多く、クライアント側スクリプトが利用できるかどうかが常に明確とは限りませんでした。  
  
 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] では、サーバー側スクリプトによって生成されたクライアント側スクリプト ファイルは、既定で表示されるソリューション エクスプローラーに表示されます。 [スクリプト エクスプローラー] ウィンドウは削除されました。  
  
 クライアント側スクリプト ファイルは、デバッグ モードまたは中断モードのときにのみ表示されます。 表示される、**スクリプト ドキュメント**ノード。  
  
 サーバー側スクリプト ファイルは常に表示されます。 表示される、  **\<web サイトのパス名 >** ノード。 ノードの名前には、この例に似ています。 `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>サーバー側スクリプト ドキュメントを表示するには  
  
1.  **ソリューション エクスプ ローラー**、オープン、  **\<web サイトのパス名 >** ノード。  
  
2.  表示するスクリプト ファイルをダブルクリックします。  
  
     サーバー側スクリプト ファイルがソース ウィンドウに表示されます。  
  
### <a name="to-view-a-client-side-script-document"></a>クライアント側スクリプト ドキュメントを表示するには  
  
1.  **ソリューション エクスプ ローラー**、オープン、**スクリプト ドキュメント**ノード。  
  
2.  表示するスクリプト ファイルをダブルクリックします。  
  
     クライアント側スクリプト ファイルがソース ウィンドウに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーでのデータ表示](../debugger/viewing-data-in-the-debugger.md)



