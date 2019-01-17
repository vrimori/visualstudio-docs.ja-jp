---
title: SDI サーバー アプリケーション |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec4178fb23d84812d7258bac8384264bed9d4690
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885062"
---
# <a name="sdi-server-applications"></a>SDI サーバー アプリケーション
SDI サーバー アプリケーションをデバッグする場合は、C/C++、C#、または Visual Basic のプロジェクトの [*プロジェクト* プロパティ ページ] ダイアログ ボックスで、**[コマンド ライン引数]** プロパティに `/Embedding` または `/Automation` を指定する必要があります。  
  
 デバッガーはこれらのコマンド ライン引数を利用して、コンテナーから起動されたようにサーバー アプリケーションを起動できます。 次に、プログラム マネージャーまたはファイル マネージャーからコンテナーを起動すると、コンテナーはデバッガー中で起動されたサーバーのインスタンスを使用できます。  
  
## <a name="finding-the-command-line-arguments-property"></a>[コマンド ライン引数] プロパティの表示  
 [*プロジェクト* プロパティ ページ] ダイアログ ボックスにアクセスするには、ソリューション エクスプローラーでプロジェクトを右クリックし、ショートカット メニューの [プロパティ] を選びます。 [コマンド ライン引数] プロパティを表示するには、[構成プロパティ] カテゴリを展開し、[デバッグ] ページをクリックします。  
  
## <a name="see-also"></a>「  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [方法: COM サーバーをデバッグする](../debugger/how-to-debug-com-servers.md)