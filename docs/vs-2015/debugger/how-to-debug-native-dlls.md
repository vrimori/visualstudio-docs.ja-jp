---
title: '方法: ネイティブ Dll のデバッグ |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 467b87c1a0e72c5523523aae015f03b54273907c
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592911"
---
# <a name="how-to-debug-native-dlls"></a>方法: ネイティブ DLL サーバーをデバッグする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: ネイティブ Dll のデバッグ](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-native-dlls)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、[ツール] メニューの [設定のインポートとエクスポート] をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 DLL をデバッグするときには、次のプロジェクトからデバッグを開始できます。  
  
-   DLL を呼び出す実行可能ファイルの作成に使用したプロジェクト  
  
 \- または -  
  
-   DLL 自身を作成するのに使用したプロジェクト  
  
 実行可能ファイルの作成に使用したプロジェクトがある場合は、そのプロジェクトからデバッグを開始します。 実行可能ファイルの作成に使用したプロジェクトに含まれていない DLL でも、そのソース ファイルを開いてブレークポイントを設定できます。 詳細については、次を参照してください。[ブレークポイント](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)します。  
  
 DLL を作成したプロジェクトからデバッグを開始する場合は、DLL のデバッグに使用する実行可能ファイルを指定する必要があります。  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>デバッグ セッション用の実行可能ファイルを指定するには  
  
1.  **ソリューション エクスプ ローラー**DLL を作成したプロジェクトを選択します。  
  
2.  **ビュー** ] メニューの [選択**プロパティ ページ**します。  
  
3.  **プロパティ ページ**ダイアログ ボックスで、**構成プロパティ**フォルダーと選択、**デバッグ**カテゴリ。  
  
4.  **コマンド**ボックスで、コンテナーのパス名を指定します。 たとえば、「C:\Program Files\MyApplication\MYAPP.EXE」のように指定します。  
  
5.  **コマンド引数**ボックスで、実行可能ファイルに必要な引数を指定します。  
  
 実行可能ファイルを指定しない場合、_プロジェクト_**プロパティ ページ** ダイアログ ボックスで、[デバッグ セッション ダイアログ ボックスの実行可能ファイル](../debugger/executable-for-debugging-session-dialog-box.md)デバッグを開始するときに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [Visual Studio でのデバッグ](../debugger/debugging-in-visual-studio.md)



