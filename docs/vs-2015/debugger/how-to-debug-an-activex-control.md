---
title: '方法: ActiveX コントロールのデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2cb1431b2be4c125b50ec45054e0d10685a2fe4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281737"
---
# <a name="how-to-debug-an-activex-control"></a>方法 : ActiveX コントロールをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 ActiveX コントロールをデバッグするには、そのコントロールが実行されるコンテナー (実行可能ファイル) を指定する必要があります。  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>デバッグ セッションのコンテナーを指定するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  **ビュー** ] メニューの [選択**プロパティ ページ**します。  
  
3.  **プロジェクト プロパティ ページ**ダイアログ ボックスで、**構成プロパティ**フォルダー、および選択**デバッグ**します。  
  
4.  で、**デバッグ**カテゴリ、検索、**コマンド**プロパティ。  
  
5.  コンテナーのパス名を指定します。 たとえば、「C:\Program Files\Internet Explorer\IEXPLORE.EXE」のように指定します。  
  
6.  Internet Explorer をコンテナーとして指定する、Active Desktop を使用している場合は、入力`/new`で、**コマンド引数**ボックス。  
  
7.  **[OK]** をクリックします。  
  
     内のコンテナーを指定しない場合、**プロジェクト プロパティ ページ**ダイアログ ボックスで、デバッグを開始するときに、コンテナーを指定できます。 デバッグを開始する実行コマンドを選択すると、[デバッグ セッション ダイアログ ボックスの実行可能ファイル](../debugger/executable-for-debugging-session-dialog-box.md)が表示されます。 ダイアログ ボックスにコンテナーのパス名を指定します。  
  
## <a name="see-also"></a>関連項目  
 [ActiveX コントロール](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [テスト コンテナーでイベントのプロパティとテスト](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM および ActiveX のデバッグ](../debugger/com-and-activex-debugging.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)



