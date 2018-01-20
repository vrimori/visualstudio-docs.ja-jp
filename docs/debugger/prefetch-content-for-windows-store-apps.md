---
title: "UWP アプリでプリフェッチ コンテンツを使用してデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 6a0555e2a3ea600a1f5b11eaf95a48f4cfd7df3e
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>UWP アプリのプリフェッチされたコンテンツを使用して、Visual Studio でのデバッグします。
  
 UWP アプリの応答性が向上するには、アプリの web ページやイメージなど、一部の web コンテンツを事前に Windows を要求することができます[WinINet](http://msdn.microsoft.com/library/0a06f2af-957a-4dff-a8cc-187370181b5c)キャッシュします。 この機能をプリフェッチと呼びます。 起動時に使用されるコンテンツに特に効果的であるが、すぎる、頻繁に使用されるその他のコンテンツをプリフェッチすることができます。 メソッド、 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher)クラスを使用して、プリロードするコンテンツの Uri を指定できます。 Windows SDK を参照して[コンテンツのプリフェッチ サンプル](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)アプリに ContentPrefetcher 機能を追加する方法の例についてはします。  
  
 Windows は、プリフェッチを行う必要がある場合およびダウンロードするリソースを決定するためにヒューリスティックを使用します。 このヒューリスティックでは、システム ネットワークおよび電力条件、ユーザー アプリの使用履歴、および以前のプリフェッチの結果を考慮します。 Visual Studio で、使用することができます、 **Trigger Windows Store App Prefetch**コマンドを Windows が ContentPrefetcher ヒューリスティックを無視し、すべて指定された web コンテンツのプリロードを強制します。 これは、既知の状態 (読み込まれている、または読み込まれていない) でプリフェッチするコンテンツでアプリの動作またはパフォーマンスをテストする場合に役立ちます。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher で指定されるリソースのプリロードを強制するには  
 この手順では、ContentPrefetcher 機能が既に設定されていて、アプリ プロジェクトでプリロードするコンテンツ URI が指定されていると仮定しています。 指定されたリソースが新しいまたは変更された場合にコンテンツのプリロードを強制するには起動しを選択する前に、アプリを停止する必要がある、 **Trigger Windows Store App Prefetch**コマンド。 まず、アプリを実行して、URI を登録します。 **Trigger Windows Store App Prefetch**コマンドによって、contentprefetcher ように、コンテンツをダウンロードしてキャッシュを追加します。 アプリの後続の実行で、コンテンツがプリロードされたと見なすことができます。  
  
1.  アプリを開始して、アプリでプリフェッチ コンテンツ URI を登録します。 **デバッグ** メニューの 選択**デバッグの開始** (キーボード ショートカット: f5 キーを押します)。  
  
2.  **デバッグ** メニューの 選択**デバッグの停止** (キーボード ショートカット: shift キーを押しながら f5 キーを押します)。  
  
3.  **デバッグ**] メニューの [選択**その他のデバッグ ターゲット**を選択し**Trigger Windows Store App Prefetch**です。  
  
 プリフェチした Web リソースでアプリをデバッグ、テスト、または分析できるようになりました。  
  
> [!NOTE]
>  指定された Web コンテンツを追加または変更するたびにこの手順を繰り返します。  
  
## <a name="see-also"></a>参照  
 [ブログの投稿: プリフェッチ Windows ストア アプリ用 Visual Studio 2013 Update 2 でトリガーします。](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)