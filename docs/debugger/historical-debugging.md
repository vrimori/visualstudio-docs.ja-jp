---
title: "デバッグ履歴 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0107109cfa5b15b8db0c84b304e8e1daae5dfbfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="historical-debugging"></a>デバッグ履歴
デバッグ履歴は、IntelliTrace で収集された情報に依存するデバッグのモードです。 アプリケーションの実行内を前後に移動して、実行の状態を調べることができます。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
## <a name="why-use-historical-debugging"></a>デバッグ履歴を使用する理由  
 ブレークポイントを設定してバグを探すのは、どちらかというと行き当たりばったりな方法です。 バグがありそうな場所のコードの近くにブレークポイントを設定し、デバッガーでアプリケーションを実行して、ブレークポイントがヒットし、実行が中断した場所でバグの原因が明らかになることを期待します。 それ以外の場合は、コードの別の場所のブレークポイントを設定してみてくださいし、問題が見つかるまで繰り返しテスト ステップを実行する、デバッガーを再実行する必要があります。  
  
 ![ブレークポイントを設定する](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 IntelliTrace とデバッグ履歴を使用して、アプリケーション内を移動して、デバッグを再起動して、ブレークポイントの設定をしなくても (呼び出し履歴およびローカル変数) の状態を検査およびテスト手順を繰り返すことができます。 これにより多くの時間を節約できます。実行に時間がかかるテスト シナリオの深い場所にバグがある場合は特に有効です。  
  
## <a name="how-do-i-start-using-historical-debugging"></a>デバッグ履歴の使用を開始する方法  
 IntelliTrace は既定で有効になります。 行う必要があるすべてが対象のイベントと関数の呼び出しをするには、関心のあるは、完全なアプリケーションの状態のスナップショットを表示するかどうかを決定します。 検索する対象の定義の詳細については、次を参照してください。 [IntelliTrace 機能の](../debugger/intellitrace-features.md)します。  

 - デバッグ履歴でのスナップショットを表示するには、次を参照してください[IntelliTrace ステップ ライトバックを使用してスナップショットを表示します。](../debugger/how-to-use-intellitrace-step-back.md)
 - 変数を検査し、コード内を移動する方法については、次を参照してください[デバッグ履歴でアプリを調べる。](../debugger/historical-debugging-inspect-app.md)
 - IntelliTrace イベントとデバッグの詳細については、次を参照してください。[チュートリアル: IntelliTrace を使用した](../debugger/walkthrough-using-intellitrace.md)です。