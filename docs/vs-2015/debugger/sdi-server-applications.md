---
title: SDI サーバー アプリケーション |Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba975d21e1fbef2d32b45dd4ebdc758e8b6cf575
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199070"
---
# <a name="sdi-server-applications"></a>SDI サーバー アプリケーション
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

かどうかは、SDI サーバー アプリケーションをデバッグしている、指定する必要あります`/Embedding`または`/Automation`で、**コマンドライン引数**プロパティ、*プロジェクト*C と C++、c# のプロパティ ページ ダイアログ ボックスまたはVisual Basic のプロジェクト。  
  
 デバッガーはこれらのコマンド ライン引数を利用して、コンテナーから起動されたようにサーバー アプリケーションを起動できます。 次に、プログラム マネージャーまたはファイル マネージャーからコンテナーを起動すると、コンテナーはデバッガー中で起動されたサーバーのインスタンスを使用できます。  
  
## <a name="finding-the-command-line-arguments-property"></a>[コマンド ライン引数] プロパティの表示  
 アクセスする、*プロジェクト*プロパティ ページ ダイアログ ボックスでは、ソリューション エクスプ ローラーでプロジェクトを右クリックし、ショートカット メニューからプロパティを選択します。 [コマンド ライン引数] プロパティを表示するには、[構成プロパティ] カテゴリを展開し、[デバッグ] ページをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [方法 : COM サーバーをデバッグする](../debugger/how-to-debug-com-servers.md)



