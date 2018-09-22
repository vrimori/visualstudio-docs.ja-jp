---
title: デバッグ履歴 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a622fcb91ad40e7d0777f37ce87e9a2cb950695
ms.sourcegitcommit: a749c287ec7d54148505978e8ca55ccd406b71ee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/21/2018
ms.locfileid: "46542404"
---
# <a name="historical-debugging"></a>デバッグ履歴
デバッグ履歴は、IntelliTrace で収集された情報に依存するデバッグのモードです。 アプリケーションの実行内を前後に移動して、実行の状態を調べることができます。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できます (Professional Edition または Community Edition の場合は使用できません)。  
  
## <a name="why-use-historical-debugging"></a>デバッグ履歴を使用する理由  
 ブレークポイントを設定してバグを探すのは、どちらかというと行き当たりばったりな方法です。 バグがありそうな場所のコードの近くにブレークポイントを設定し、デバッガーでアプリケーションを実行して、ブレークポイントがヒットし、実行が中断した場所でバグの原因が明らかになることを期待します。 有効でない場合は、コード内のどこか他のブレークポイントを設定してくださいし、問題が見つかるまで繰り返しテスト手順を実行して、デバッガーを再実行する必要があります。  
  
 ![ブレークポイントを設定する](../debugger/media/breakpointprocesa.png "BreakpointProcesa")  
  
 IntelliTrace とデバッグ履歴を使用して、アプリケーション内を移動して、デバッグを再起動して、ブレークポイントの設定をしなくても (呼び出し履歴およびローカル変数) の状態を検査し、テスト手順を繰り返すことができます。 これにより多くの時間を節約できます。実行に時間がかかるテスト シナリオの深い場所にバグがある場合は特に有効です。  
  
## <a name="how-do-i-start-using-historical-debugging"></a>デバッグ履歴の使用を開始する方法  
 IntelliTrace は既定で有効になります。 行う必要があるすべてが対象のイベントと関数の呼び出しは、関心のあるし、の完全なアプリケーション状態のスナップショットを表示するかどうかを決定します。 検索する対象の定義の詳細については、次を参照してください。 [IntelliTrace 機能](../debugger/intellitrace-features.md)します。  

 - デバッグ履歴のスナップショットを表示するを参照してください[IntelliTrace を使用して前のアプリ状態を調べる。](../debugger/view-historical-application-state.md)
 - 変数を検査して、コードを移動する方法については、次を参照してください[デバッグ履歴を使用してアプリを調べる。](../debugger/historical-debugging-inspect-app.md)
 - IntelliTrace イベントでのデバッグの詳細については、次を参照してください。[チュートリアル: IntelliTrace を使用した](../debugger/walkthrough-using-intellitrace.md)します。