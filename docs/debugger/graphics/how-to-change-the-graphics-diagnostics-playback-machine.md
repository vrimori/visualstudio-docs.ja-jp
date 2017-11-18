---
title: "方法: グラフィックス診断再生マシンを変更する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35b8eb174ea8e0ca238bafe5a05dfbba54855cda
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>方法: グラフィックス診断再生マシンを変更する
ローカル コンピューターを使用するか、リモート コンピューターまたはリモート デバイスを使用して、グラフィックス情報を再生できます。  
  
## <a name="choosing-a-playback-machine"></a>再生コンピューターの選択  
 再生コンピューターは、グラフィックス ログからグラフィックス イベントを再生するために使用されるコンピューターまたはデバイスです。 通常はローカル コンピューターが最も便利ですが、レンダリングの問題は、問題がキャプチャされたコンピューターとはハードウェアやドライバーのバージョンが異なるコンピューターで再現しない場合があります。その場合は、問題を適切に再現するリモート再生コンピューターを選択し、開発用コンピューターを使用して診断することができます。  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>ローカル コンピューターを使用してグラフィックス情報を再生するには  
  
1.  グラフィックス ログ ドキュメント ウィンドウで、選択、**再生コンピューター**リンクします。 **リモート デバッガー接続** ダイアログ ボックスが表示されます。  
  
2.  **手動で構成**で、**アドレス**プロパティ、入力`localhost`です。  
  
3.  設定、**認証モード**プロパティを**None**です。  
  
4.  選択、**選択**ボタンをクリックします。  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>リモート コンピューターを使用してグラフィックス情報を再生するには  
  
1.  グラフィックス ログ ドキュメント ウィンドウで、選択、**再生コンピューター**リンクします。 **リモート デバッガー接続** ダイアログ ボックスが表示されます。  
  
2.  **手動で構成**で、**アドレス**プロパティ、Windows ドメイン名またはコンピューターやグラフィックス情報を再生に使用するデバイスの IP アドレスを入力します。  
  
3.  再生コンピューターへの接続を保護するために使用する承認の種類を指定します。  
  
    -   Windows 認証を設定、**認証モード**プロパティを**Windows**です。  
  
    -   認証なしは、設定、**認証モード**プロパティを**None**です。  
  
4.  選択、**選択**ボタンをクリックします。  
  
> [!NOTE]
>  **リモート デバッガー接続** ダイアログ ボックスは、開発用コンピューターに直接接続されている、または同じサブネット上のリモート デバッグ ターゲットを表示も可能性があります。 これらのリモート デバッグ ターゲットのいずれかを、手動で構成せずに、グラフィックス診断再生コンピューターとして使用できます。 **リモート デバッガー接続** ダイアログ ボックスで、選択してを選択し、ターゲット、**選択**ボタンをクリックします。  
  
## <a name="see-also"></a>関連項目  
 [グラフィックス ログ ドキュメント](graphics-log-document.md)