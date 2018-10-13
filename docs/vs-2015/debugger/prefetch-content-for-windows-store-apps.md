---
title: Windows ストア アプリ用コンテンツのプリフェッチ |Microsoft Docs
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
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9329cad2f0125288aeea146070188d023d1a126
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211446"
---
# <a name="prefetch-content-for-windows-store-apps"></a>Windows ストア アプリ用コンテンツのプリフェッチ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows にのみ適用されます] (../Image/windows_only_content.png"windows_only_content")  
  
 Windows ストア アプリの応答性が向上するには、アプリの web ページやイメージなど、一部の web コンテンツを事前に Windows を要求することができます[WinINet](http://msdn.microsoft.com/en-us/0a06f2af-957a-4dff-a8cc-187370181b5c)[WinINet](http://msdn.microsoft.com/library/aa383630.aspx)キャッシュします。 この機能をプリフェッチと呼びます。 これは起動時に使用されるコンテンツに特に効果的ですが、他の頻繁に使用するコンテンツをプリフェッチすることもできます。 メソッド、 [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx)クラスを使用して、プリロードするコンテンツの Uri を指定できます。 Windows SDK を参照して[コンテンツのプリフェッチ サンプル](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309)をアプリに ContentPrefetcher 機能を追加する方法の例についてはします。  
  
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
 [ブログの投稿: プリフェッチ Windows ストア アプリ用 Visual Studio 2013 Update 2 をトリガーします。](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)



