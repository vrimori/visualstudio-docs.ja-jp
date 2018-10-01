---
title: IntelliTrace の機能 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliTrace, debugging with events
- IntelliTrace, recording execution history
- debugging [Visual Studio ALM], recording execution history
- IntelliTrace, turn off
- IntelliTrace, navigating event and call history
- IntelliTrace, saving your session
- IntelliTrace, enabling
- IntelliTrace, start debugging
- IntelliTrace, debugging with events and call information
- IntelliTrace, disabling
- IntelliTrace, turn on
- debugging [Visual Studio ALM], IntelliTrace
ms.assetid: 5ccc059c-6097-46b4-9d4b-34236c02d549
caps.latest.revision: 73
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15b58b80a3ab3c9ae1a515eda82a946d56c0554d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538875"
---
# <a name="intellitrace-features"></a>IntelliTrace の機能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IntelliTrace 機能](https://docs.microsoft.com/visualstudio/debugger/intellitrace-features)します。  
  
IntelliTrace を使用すると、イベントとアプリケーションを呼び出すメソッドとを記録することができます。この機能により、さまざまな実行ポイントでの状態 (呼び出し履歴およびローカル変数の値) を確認することができます。 通常どおりにデバッグを開始 - 既定では、IntelliTrace がオンし、IntelliTrace の記録で、新しい情報を確認できます**診断ツール**] ウィンドウの [、**イベント**タブ。イベントを選択し、をクリックして**履歴デバッグの有効化**呼び出し履歴とローカル変数のこのイベントの記録を確認します。  
  
 ステップ バイ ステップの説明を参照してください。[チュートリアル: IntelliTrace を使用した](../debugger/walkthrough-using-intellitrace.md)します。  
  
 IntelliTrace は Visual Studio Enterprise Edition で使用できますが、Visual Studio Professional Edition または Community Edition では使用できません。  
  
 IntelliTrace がオンになっていることを確認するを開き、**ツール/オプション/IntelliTrace**オプション ページ。 **IntelliTrace を有効にする**既定でオンにする必要があります。  
  
> [!NOTE]
>  すべての設定のスコープ、 **IntelliTrace**オプション ページでは、Visual Studio を全体、個々 のプロジェクトまたはソリューションとして。 これらの設定に加えた変更は、Visual Studio のすべてのインスタンス、すべてのデバッグ セッション、あるいはすべてのプロジェクトまたはソリューションに適用されます。  
  
##  <a name="ChooseEvents"></a> IntelliTrace で記録するイベントを選択します。  
 特定の IntelliTrace イベントの記録はオンまたはオフにすることができます。  
  
 デバッグ中の場合、デバッグを停止します。 移動して**ツール/オプション/IntelliTrace/IntelliTrace イベント**します。 IntelliTrace で記録するイベントを選択します。  
  
##  <a name="GoingFurther"></a> IntelliTrace イベントの収集し、呼び出し情報  
 このオプションは既定では有効になっていませんが、IntelliTrace ではイベントと共にメソッドの呼び出しを記録できます。 呼び出しメソッドのコレクションを有効にする**ツール/オプション/IntelliTrace/[全般]**、選択と**IntelliTrace イベントと呼び出し情報**します。  
  
 これにより、呼び出し履歴が表示され、コード内で呼び出しの前後を移動できるようになります。 IntelliTrace は、メソッド名、メソッド エントリ、および終了ポイントなどのデータと、特定のパラメーター値および戻り値を記録します。  
  
> [!TIP]
>  このオプションは既定では有効になっていません。かなりのオーバーヘッドが追加されるためです。 IntelliTrace はアプリケーションが行うすべてのメソッド呼び出しを先に取得する必要があるだけでなく、それを画面に表示したりディスクに保存したりする上で大量のデータ セットを処理する必要があります。  
>   
>  パフォーマンスのオーバーヘッドは、IntelliTrace で記録するイベントの一覧を制限することで、さらに収集するモジュール数を最小限に抑えることで、減らすことができます。 詳細については、次を参照してください。[コントロール量呼び出し情報 IntelliTrace が記録](../debugger/intellitrace-features.md#ControlCallData)します。  
  
### <a name="using-the-navigation-gutter"></a>ナビゲーション余白を使用する  
 コード ウィンドウの左側に表示されるナビゲーション余白を使用することができます。 ナビゲーション余白が表示されない場合は、**ツール/オプション/IntelliTrace/高度な**、選択と**デバッグ モードでナビゲーション余白を表示**します。  
  
 ナビゲーション余白を使用すれば、デバッグ履歴モードでメソッド呼び出しとイベントの中を前後に移動することができます。 デバッグ履歴の詳細については、次を参照してください。[デバッグ履歴](../debugger/historical-debugging.md)します。 以下のようなコマンドがあります。  
  
|||  
|-|-|  
|**デバッガー コンテキストをここで設定します。**|これが表示される呼び出しタイム フレームにデバッグ コンテキストを設定します。<br /><br /> このアイコンは、現在の呼び出し履歴にのみ表示されます。|  
|**呼び出しサイトに戻る**|ポインターとデバッグ コンテキストを現在の関数が呼び出された場所に戻します。<br /><br /> ライブ デバッグ モードの場合は、このコマンドでデバッグ履歴をオンにします。 元の実行中断場所に戻ると、デバッグ履歴はオフになり、ライブ デバッグがオンになります。|  
|**前の呼び出しまたは IntelliTrace イベントへ移動します。**|ポインターとデバッグ コンテキストを前の呼び出しまたはイベントに戻します。<br /><br /> ライブ デバッグ モードの場合は、このコマンドでデバッグ履歴をオンにします。|  
|**ステップ イン**|現在選択されている関数にステップインします。<br /><br /> このコマンドは、デバッグ履歴モード中にのみ使用できます。|  
|**次の呼び出しまたは IntelliTrace イベントへ移動します。**|ポインターとデバッグ コンテキストを IntelliTrace データが存在する次の呼び出しまたはイベントまで進めます。<br /><br /> このコマンドは、デバッグ履歴モード中にのみ使用できます。|  
|**ライブ モードへ移動**|ライブ デバッグ モードに戻ります。|  
  
### <a name="search-for-a-line-or-method-in-intellitrace"></a>行またはメソッドを IntelliTrace で検索する  
 メソッドを検索できるのは、メソッド呼び出し情報が有効になっている場合に限られます。 特定の行またはメソッドの IntelliTrace 履歴を検索することができます。 デバッガーの実行が停止したときに、コンテキスト メニューを表示するには、関数の本体内部で右クリックし、いずれかをクリックして**IntelliTrace でこの行の検索**または**IntelliTrace でこのメソッドの検索**します。  
  
###  <a name="ControlCallData"></a> どの程度呼び出し情報の IntelliTrace の記録を制御します。  
 既定では、IntelliTrace はソリューションで使用されるすべてのモジュールについて情報を記録します。 関心のあるモジュールに関してのみ、呼び出し情報を記録するように IntelliTrace を設定できます。 **ツール/オプション/IntelliTrace/モジュール**、含めるモジュールまたは IntelliTrace から除外するモジュールを指定できます。 指定したモジュールから発生したイベントと、関心のあるモジュール内で発生したメソッド呼び出しだけが IntelliTrace で収集されます。  
  
 複数のモジュールを追加するには、ワイルドカード文字 * を文字列の先頭または末尾に使用します。 モジュール名には、アセンブリ名ではなくファイル名を使用してください。 ファイル パスは使用できません。  
  
 モジュールの数は最小限に抑えるようにしてください。 そうすれば、収集するデータが少なくなるので、パフォーマンスが向上します。 また、処理すべきデータが少なくなるので、UI のノイズが減少します。  
  
##  <a name="SaveSession"></a> IntelliTrace データをファイルに保存します。  
 IntelliTrace で収集されたデータを保存することができますを**デバッグ/IntelliTrace IntelliTrace セッションの保存/** をデバッグすると、アプリケーションがブレーク状態にします。 アプリケーションがまだ実行中の場合またはデバッグが停止状態の場合、メニュー項目は無効であるため、IntelliTrace で収集されたデータを保存することはできません。  
  
 移動してファイルに自動的に保存するように IntelliTrace を構成することができます**ツール/オプション/IntelliTrace、高度な**を選択して**ストア IntelliTrace 記録をこのディレクトリに**。 生成するファイルの設定サイズを構成することもできます。その場合、IntelliTrace は領域が足りなくなると古いデータから順に上書きしていきます。 Visual Studio では、ファイルが自動保存されるときと Visual Studio のホスティング プロセス (vshost.exe) をオンにしたときに、IntelliTrace セッションごとに 2 つのファイルが作成されます。  
  
> [!TIP]
>  ファイルが必要なくなった場合は、ディスク領域を節約するためにファイルの保存を自動的にオフにします。 既存のファイルは削除されません。 いつでも必要に応じてコンテキスト メニューからファイルに保存することができます。  
  
 IntelliTrace データをファイルに保存する場合は、IntelliTrace が収集対象としたプロセスごとに 1 つの .itrace ファイルが得られます。 移動して、Visual Studio で、.itrace ファイルを開くことができますし、 **/ファイルのファイル/を開く**ファイルを開くダイアログ ボックスから .itrace ファイルを選択します。 詳細については、次を参照してください。[保存された IntelliTrace データを使用して](../debugger/using-saved-intellitrace-data.md)します。  
  
## <a name="blogs"></a>ブログ  
 [IntelliTrace in Visual Studio Enterprise 2015 (Visual Studio Enterprise2015 の IntelliTrace)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/intellitrace-in-visual-studio-ultimate-2015.aspx)  
  
 [ライブ デバッグのチュートリアル IntelliTrace を使用して、Visual Studio 2015 (テキスト エディター)](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-text-editor.aspx)  
  
 [ライブ デバッグのチュートリアルでは、Visual Studio 2015 (ソーシャル クラブ) IntelliTrace を使用します。](http://blogs.msdn.com/b/visualstudioalm/archive/2000/1/1/walkthrough-of-live-debugging-using-intellitrace-in-visual-studio-2015-social-club.aspx)  
  
 [サポートしているアタッチの Visual Studio Enterprise 2015 の IntelliTrace を!](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/intellitrace-in-visual-studio-enterprise-2015-now-supports-attach.aspx)  
  
 [IntelliTrace スタンドアロン コレクターを使用して windows サービスからデータを収集します。](http://blogs.msdn.com/b/visualstudioalm/archive/2015/05/14/collect-data-from-a-windows-service-using-the-intellitrace-standalone-collector.aspx)  
  
 [IntelliTrace 収集計画の編集](http://blogs.msdn.com/b/visualstudioalm/archive/2015/03/09/editing-the-intellitrace-collection-plan.aspx)  
  
 [カスタム TraceSource と IntelliTrace を使用したデバッグ](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/17/custom-tracesource-and-debugging-using-intellitrace.aspx)  
  
 [Active Directory アカウントで実行中の IntelliTrace スタンドアロン コレクターとアプリケーション プール](http://blogs.msdn.com/b/visualstudioalm/archive/2014/12/22/intellitrace-standalone-collector-and-application-pools-running-under-active-directory-accounts.aspx)  
  
## <a name="forums"></a>フォーラム  
 [Visual Studio デバッガー](http://go.microsoft.com/fwlink/?LinkId=262263)  
  
## <a name="videos"></a>ビデオ  
 [IntelliTrace エクスペリエンス](https://channel9.msdn.com/Series/Visual-Studio-2015-Enterprise-Videos/IntelliTrace-Experience)  
  
 [Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/events/Ignite/2015/BRK3716)





