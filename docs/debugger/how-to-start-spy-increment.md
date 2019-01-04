---
title: '方法: Spy++ を起動 |Microsoft Docs'
ms.custom: ''
ms.date: 12/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5143c34f0c344fecec82a5d08b2e7fb9b95ac1bc
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646868"
---
# <a name="how-to-start-spy"></a>方法: Spy++ の起動

開始できます spy++ コマンド プロンプトまたは Visual Studio から。  
  
 開始すると、spy++、コンピューターに変更するアクセス許可を要求するメッセージが表示されている場合**はい**します。  
  
> [!NOTE]
>  Spy++ の 1 つだけのインスタンスを実行することができます。 2 番目のインスタンスを開始しようとする場合だけ、フォーカスを取得する現在実行中のインスタンスが発生します。

## <a name="prerequisites"></a>必須コンポーネント

Spy++ は、次のコンポーネントが必要です。 選択すると、Visual Studio インストーラーからこれらのコンポーネントを選択することができます、**個々 のコンポーネント**タブをクリックし、次のコンポーネントを選択します。

* デバッグとテスト選択**C++ のプロファイル ツール**
* 開発アクティビティで、次のように選択します**Visual Studio c コア機能。**

変更を加えた場合は、これらのコンポーネントのインストールを指示します。
  
## <a name="start-spy-from-visual-studio"></a>Visual Studio から spy++ を起動します。
  
**ツール**メニューの  **spy++** します。  
  
Spy++ が実行されるためいない、独立して開始した後は、Visual Studio を閉じることができます。  
  
> [!NOTE]
>  ログ メッセージを Spy++ では、オペレーティング システムのパフォーマンスが低下することがあります。  
  
## <a name="start-spy-at-a-command-prompt"></a>コマンド プロンプトで spy++ を起動します。  
  
1.  コマンド プロンプト ウィンドウで、spyxx.exe を含むフォルダーにディレクトリを変更します。 通常、このフォルダーへのパスには.\\ *Visual Studio インストール フォルダー*\Common7\Tools\\します。  
  
2.  入力**spyxx.exe**します。 
  
## <a name="see-also"></a>関連項目  
 [Spy++ の使用](../debugger/using-spy-increment.md)   
 [Spy++ ビュー](../debugger/spy-increment-views.md)   
 [Spy++ リファレンス](../debugger/spy-increment-reference.md)