---
title: '方法: ActiveX コントロールのデバッグ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f036809024ff5489c36dbe4ff266d361b96ca294
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-an-activex-control"></a>方法 : ActiveX コントロールをデバッグする
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 ActiveX コントロールをデバッグするには、そのコントロールが実行されるコンテナー (実行可能ファイル) を指定する必要があります。  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>デバッグ セッションのコンテナーを指定するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  **ビュー** ] メニューの [選択**プロパティ ページ**です。  
  
3.  **プロジェクト プロパティ ページ** ダイアログ ボックスで、**構成プロパティ**フォルダー、および選択**デバッグ**です。  
  
4.  下にある、**デバッグ**カテゴリで、検索、**コマンド**プロパティです。  
  
5.  コンテナーのパス名を指定します。 たとえば、「C:\Program Files\Internet Explorer\IEXPLORE.EXE」のように指定します。  
  
6.  Internet Explorer をコンテナーとして指定する、アクティブ デスクトップを使用している場合は、入力`/new`で、**コマンド引数**ボックス。  
  
7.  **[OK]**をクリックします。  
  
     内のコンテナーを指定しない場合、**プロジェクト プロパティ ページ**ダイアログ ボックスで、デバッグを開始するときに、コンテナーを指定できます。 デバッグを開始する実行コマンドを選択すると、[デバッグ セッション ダイアログ ボックスの実行可能ファイル](../debugger/executable-for-debugging-session-dialog-box.md)が表示されます。 ダイアログ ボックスにコンテナーのパス名を指定します。  
  
## <a name="see-also"></a>関連項目  
 [ActiveX コントロール](/cpp/mfc/activex-controls)   
 [テスト コンテナーでイベントのプロパティとテスト](/cpp/mfc/testing-properties-and-events-with-test-container)   
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [Visual Studio でのデバッグ](../debugger/index.md)  
 [デバッガー機能ツアー](../debugger/debugger-feature-tour.md)