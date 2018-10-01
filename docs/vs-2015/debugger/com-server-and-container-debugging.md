---
title: COM サーバーおよびコンテナーのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 531c485f50a4a775ca2933c40f5ff74ca9c43717
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539680"
---
# <a name="com-server-and-container-debugging"></a>COM サーバーおよび COM コンテナーのデバッグ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[COM サーバーおよびコンテナーのデバッグ](https://docs.microsoft.com/visualstudio/debugger/com-server-and-container-debugging)します。  
  
COM アプリケーションは、プログラマが直接コントロールできないところで多くのタスクを実行します。 DLL 間の通信、オブジェクトの使用数のカウント、クリップボード処理などは、予期せぬ動作に遭遇する領域のほんの一例です。 このような事態が発生した場合は、まず問題の原因を追及します。  
  
 Visual Studio のデバッガーは、コンテナーやサーバー間のステップやステップ インをサポートしています。 この機能には、リモート プロシージャ コール (RPC) 間のステップも含まれます。  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> COM サーバーと同じソリューション内のコンテナーのデバッグ  
 同じソリューションで 2 つのプロジェクトを使用して、COM サーバーおよび COM コンテナーをデバッグできます。 それぞれのプロジェクトに適切なブレークポイントを設定してデバッグを行います。 ブレークポイントが設定されているサーバーをコンテナーが呼び出すと、サーバーのコードに戻るまで、つまりデバッグが終了するまで、コンテナーは待機しています。  
  
 COM コンテナーのデバッグは、標準的なプログラムのデバッグによく似ています。 違いがあるのは、コンテナー アプリケーションにデータをドラッグするなど、コールバックを生成するイベントをデバッグする場合です。 この場合は、ブレークポイントをコールバック関数の中に設定する必要があります。  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> コンテナー情報のないサーバー アプリケーションのデバッグ  
 コンテナー アプリケーションのデバッグ情報が不要な場合、サーバー アプリケーションは次の 3 つの手順でデバッグします。  
  
1.  サーバーのデバッグを通常のアプリケーションと同様に開始します。  
  
2.  必要な場所にブレークポイントを設定します。  
  
3.  コンテナー アプリケーションを起動します。  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> サーバーおよびドメインの分離 (SDI) アプリケーションのデバッグ  
 かどうかは、SDI サーバー アプリケーションをデバッグしている、指定する必要あります`/Embedding`または`/Automation`で、**コマンドライン引数**プロパティ、*プロジェクト*C と C++、c# のプロパティ ページ ダイアログ ボックスまたはVisual Basic のプロジェクト。  
  
 デバッガーはこれらのコマンド ライン引数を利用して、コンテナーから起動されたようにサーバー アプリケーションを起動できます。 次に、プログラム マネージャーまたはファイル マネージャーからコンテナーを起動すると、コンテナーはデバッガー中で起動されたサーバーのインスタンスを使用できます。  
  
 アクセスする、*プロジェクト*プロパティ ページ ダイアログ ボックスでは、ソリューション エクスプ ローラーでプロジェクトを右クリックし、ショートカット メニューからプロパティを選択します。 [コマンド ライン引数] プロパティを表示するには、[構成プロパティ] カテゴリを展開し、[デバッグ] ページをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)



