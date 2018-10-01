---
title: '方法: グラフィックス診断再生マシンを変更 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e33d2acc46cbf92c9b2bbd699903ad3169661a54
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538308"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>方法: グラフィックス診断再生マシンを変更する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: グラフィックス診断再生マシンを変更](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-change-the-graphics-diagnostics-playback-machine)します。  
  
ローカル コンピューターを使用するか、リモート コンピューターまたはリモート デバイスを使用して、グラフィックス情報を再生できます。  
  
## <a name="choosing-a-playback-machine"></a>再生コンピューターの選択  
 再生コンピューターは、グラフィックス ログからグラフィックス イベントを再生するために使用されるコンピューターまたはデバイスです。 通常はローカル コンピューターが最も便利ですが、レンダリングの問題は、問題がキャプチャされたコンピューターとはハードウェアやドライバーのバージョンが異なるコンピューターで再現しない場合があります。その場合は、問題を適切に再現するリモート再生コンピューターを選択し、開発用コンピューターを使用して診断することができます。  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>ローカル コンピューターを使用してグラフィックス情報を再生するには  
  
1.  グラフィックス ログ ドキュメント ウィンドウで、選択、**再生コンピューター**リンク。 **リモート デバッガー接続** ダイアログ ボックスが表示されます。  
  
2.  **手動構成**で、**アドレス**プロパティ、入力`localhost`します。  
  
3.  設定、**認証モード**プロパティを**None**します。  
  
4.  選択、**選択**ボタンをクリックします。  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>リモート コンピューターを使用してグラフィックス情報を再生するには  
  
1.  グラフィックス ログ ドキュメント ウィンドウで、選択、**再生コンピューター**リンク。 **リモート デバッガー接続** ダイアログ ボックスが表示されます。  
  
2.  **手動構成**の**アドレス**プロパティ、Windows ドメイン名またはコンピューターまたはグラフィックス情報を再生に使用するデバイスの IP アドレスを入力します。  
  
3.  再生コンピューターへの接続を保護するために使用する承認の種類を指定します。  
  
    -   Windows 認証では、設定、**認証モード**プロパティを**Windows**します。  
  
    -   認証なしは、設定、**認証モード**プロパティを**None**します。  
  
4.  選択、**選択**ボタンをクリックします。  
  
> [!NOTE]
>  **リモート デバッガー接続** ダイアログ ボックスは、開発用コンピューターに直接接続されてが同じサブネット上またはリモートのデバッグ ターゲットを表示も可能性があります。 これらのリモート デバッグ ターゲットのいずれかを、手動で構成せずに、グラフィックス診断再生コンピューターとして使用できます。 **リモート デバッガー接続** ダイアログ ボックスで、クリックして、ターゲットを選択、**選択**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [グラフィックス ログ ドキュメント](../debugger/graphics-log-document.md)



