---
title: UWP アプリでプリフェッチされたコンテンツを使用したデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: d511934dc185ed6dac8034ee3e149391b2dd185e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281547"
---
# <a name="debug-uwp-apps-using-prefetched-content-in-visual-studio"></a>プリフェッチされたコンテンツを使用して、Visual Studio で UWP アプリをデバッグします。
  
 UWP アプリの応答性が向上するには、アプリの web ページやイメージなど、一部の web コンテンツを事前に Windows を要求することができます[WinINet](/windows/desktop/WinInet/about-wininet)キャッシュします。 この機能をプリフェッチと呼びます。 起動時に使用されるコンテンツに特に効果的ですが、すぎる、頻繁に使用されるその他のコンテンツをプリフェッチすることができます。 メソッド、 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](/uwp/api/Windows.Networking.BackgroundTransfer.ContentPrefetcher)クラスを使用して、プリロードするコンテンツの Uri を指定できます。 Windows SDK を参照して[コンテンツのプリフェッチ サンプル](https://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)をアプリに ContentPrefetcher 機能を追加する方法の例についてはします。  
  
 Windows は、プリフェッチを行う必要がある場合およびダウンロードするリソースを決定するためにヒューリスティックを使用します。 このヒューリスティックでは、システム ネットワークおよび電力条件、ユーザー アプリの使用履歴、および以前のプリフェッチの結果を考慮します。 Visual Studio で使用することができます、 **Trigger Windows Store App Prefetch** Windows が ContentPrefetcher ヒューリスティックを無視して、すべて指定された web コンテンツのプリロードを強制するコマンド。 これは、既知の状態 (読み込まれている、または読み込まれていない) でプリフェッチするコンテンツでアプリの動作またはパフォーマンスをテストする場合に役立ちます。  
  
## <a name="to-force-preloading-of-contentprefetcher-specified-resources"></a>ContentPrefetcher で指定されるリソースのプリロードを強制するには  
 この手順では、ContentPrefetcher 機能が既に設定されていて、アプリ プロジェクトでプリロードするコンテンツ URI が指定されていると仮定しています。 指定されたリソースが新しいまたは変更されたときに、コンテンツのプリロードを強制的は、開始および選択する前に、アプリを停止する必要がある、 **Trigger Windows Store App Prefetch**コマンド。 まず、アプリを実行して、URI を登録します。 **Trigger Windows Store App Prefetch**コマンドには、コンテンツをダウンロードし、キャッシュに追加して ContentPrefetcher しにより適用されます。 アプリの後続の実行で、コンテンツがプリロードされたと見なすことができます。  
  
1.  アプリを開始して、アプリでプリフェッチ コンテンツ URI を登録します。 **デバッグ** メニューの 選択**デバッグの開始** (キーボード ショートカット: F5)。  
  
2.  **デバッグ** メニューの 選択**デバッグの停止** (キーボード ショートカット: shift キーを押しながら f5 キー)。  
  
3.  **デバッグ**] メニューの [選択**その他のデバッグ ターゲット**選び、 **Trigger Windows Store App Prefetch**します。  
  
 プリフェチした Web リソースでアプリをデバッグ、テスト、または分析できるようになりました。  
  
> [!NOTE]
>  指定された Web コンテンツを追加または変更するたびにこの手順を繰り返します。  
  
## <a name="see-also"></a>関連項目  
 [ブログの投稿: プリフェッチ Windows ストア アプリ用 Visual Studio 2013 Update 2 をトリガーします。](https://blogs.msdn.microsoft.com/devops/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2/)