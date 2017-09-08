---
title: "Visual Studio の起動時間の最適化 | Microsoft Docs"
ms.custom: 
ms.date: 8/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 4
author: mikejo
ms.author: mikejo
manager: ghogen
f1_keywords:
- vs.performancecenter
ms.translationtype: HT
ms.sourcegitcommit: 4306111cd49a5299bfa5d4e5e22b212bc7799fe2
ms.openlocfilehash: 8e419de02104d30344b32e28174bd7de41f91677
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---

# <a name="optimize-visual-studio-startup-time"></a>Visual Studio の起動時間の最適化
Visual Studio は常に、可能な限り迅速に起動することが理想的です。 ただし、Visual Studio 拡張機能と開いているツール ウィンドウは、起動時に自動的に読み込まれるため、起動時間に悪影響を与える可能性があります。 **[Visual Studio のパフォーマンスの管理]** ウィンドウでは、Visual Studio の起動時間に影響する拡張機能と機能を確認できるだけでなく、それらの読み込み動作を制御することもできます。

パフォーマンスの向上に関するより一般的なヒントについては、「[Visual Studio のパフォーマンスのヒントとテクニック](../ide/visual-studio-performance-tips-and-tricks.md)」を参照してください。

## <a name="control-startup-behavior"></a>起動の動作の制御

起動時間が長くならないように、Visual Studio 2017 は、要求に応じて読み込む方法を使用して、起動時に拡張機能が読み込まれないようにします。 この動作は、Visual Studio の起動後すぐに拡張機能を開くのではなく、起動後、必要に応じて開くことを意味します。 また、前の Visual Studio セッションでツール ウィンドウが開いたままである場合、スタートアップ時間が長くなる可能性があるため、Visual Studio は起動時間に影響しないようにより合理的な方法でツール ウィンドウを開きます。

Visual Studio で起動の遅延が検出されると、ポップアップ メッセージが表示され、拡張機能またはツール ウィンドウが原因で遅延が発生していることを警告します。 メッセージには **[Visual Studio のパフォーマンスの管理]** ダイアログ ボックスへのリンクも表示されます。 このウィンドウは、メニュー コマンドの **[ヘルプ] > [Visual Studio のパフォーマンスの管理]** を使用して開くこともできます。

![Visual Studio のパフォーマンスの管理 - "拡張機能...によって Visual Studio の速度が遅くなっていることを検出しました。" という内容のポップアップ](../ide/media/vside_perfdialog_popup.png)

ダイアログ ボックスには、起動のパフォーマンスに影響している拡張機能とツール ウィンドウが一覧されます。 このダイアログ ボックスでは、起動時のパフォーマンスを向上させるために拡張機能とツール ウィンドウの設定を変更することができます。

### <a name="change-extension-settings"></a>拡張機能の設定を変更する

拡張機能が Visual Studio の起動の遅延の原因となっている場合、いずれかの種類の拡張機能を選択したときに、**[Visual Studio のパフォーマンスを管理]** ダイアログ ボックスに拡張機能が表示されます。 このダイアログ ボックスには、起動時、ソリューションの読み込み時、エディターでの入力時のパフォーマンスに影響を及ぼす拡張機能が表示されます。

![Visual Studio のパフォーマンスの管理 - 拡張機能の表示](../ide/media/vside_perfdialog_extensions.png)

起動、ソリューションの読み込み、または入力の時間のそれぞれに対する影響が許容範囲を超えている場合は、**[無効にする]** ボタンを選択し、シナリオに対して拡張機能を無効にします。 拡張機能マネージャーまたは [Visual Studio のパフォーマンスの管理] ダイアログ ボックスを使用すれば、今後のセッションでいつでも拡張機能を再度有効にすることができます。

### <a name="change-tool-window-settings"></a>ツール ウィンドウの設定を変更する

ツール ウィンドウが Visual Studio の起動の遅延の原因となっている場合は、**既定の動作を使用する**のではなく、次の 2 つのオプションのいずれかを選択して、動作を上書きすることができます。

- **起動時にウィンドウを表示しない:** Visual Studio を次に開いたときに、指定したツール ウィンドウが常に閉じられます。前のセッションで開いたままの場合でも同じです。 ツール ウィンドウは対応するメニューから開くことができます。
- **起動時にウィンドウを自動的に隠す:** ツール ウィンドウが前のセッションで開いたままの場合、このオプションを選択すると、起動時にツール ウィンドウのグループが折りたたまれ、ツール ウィンドウが初期化されないようになります。 このオプションは、ツール ウィンドウがまだ使用可能でも、Visual Studio の起動時間には悪影響しなくなるため、ツール ウィンドウを頻繁に使用する場合に適しています。

![Visual Studio のパフォーマンスの管理 - ツール ウィンドウの表示](../ide/media/vside_perfdialog_toolwindows.png)

いつでもこのダイアログ ボックスに戻って、特定のツール ウィンドウの設定を変更することができます。

## <a name="speed_up_solution_load"></a>Visual Studio 2017 で大規模なソリューションを高速で読み込む

Visual Studio 2017 には、ライトウェイト ソリューション ロードという新しい機能が導入されています。これにより、IDE で大規模なソリューションを読み込む場合に必要な時間とメモリの量を減らすことができます。 多くの C#、VB、または C++ プロジェクトを含む大規模なソリューションがある場合に、ライトウェイト ソリューション ロードを有効にすると、パフォーマンスが大幅に向上する可能性があります。 この機能を使用するメリットの詳細については、[ソリューションの読み込みの最適化](../ide/optimize-solution-loading-in-visual-studio)に関する記事をご覧ください。

> [!NOTE]
> このコンテンツは Visual Studio 2017 Update 3 に適用されます。

### <a name="enable-or-disable-lightweight-solution-load"></a>ライトウェイト ソリューション ロードを有効または無効にする

ソリューション エクスプローラーでソリューション名を右クリックし、**[ライトウェイト ソリューション ロードを有効にする]** を選択します。 オプションを選択した後、ライトウェイト ソリューション ロードをアクティブ化するには、ソリューションを閉じてもう一度開く必要があります。

![ソリューション エクスプローラー](../ide/media/VSIDE_LSL_Solution_Setting.png)

ライトウェイト ソリューション ロードのグローバル設定を構成する方法については、[ソリューションの読み込みの最適化](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings)に関する記事をご覧ください。

## <a name="see-also"></a>関連項目
[Visual Studio のパフォーマンスのヒントとテクニック](../ide/visual-studio-performance-tips-and-tricks.md)

