---
title: '方法: ビルド出力ディレクトリの変更 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d8ee4bac6f04515439f5703fe2f98546e011af4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777366"
---
# <a name="how-to-change-the-build-output-directory"></a>方法: ビルド出力ディレクトリを変更する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

プロジェクトによって生成された (デバッグ、リリース、またはその両方の) 構成ごとに出力の場所を指定できます。  
  
> [!NOTE]
>  **セットアップ** プロジェクトがある場合は、この記事の最後にあるメモを参照してください。  
  
## <a name="changing-the-build-output-directory"></a>ビルド出力ディレクトリの変更  
  
#### <a name="to-change-the-build-output-directory"></a>ビルド出力ディレクトリを変更するには  
  
1.  メニュー バーで、 **[プロジェクト]**、[ *Appname* **のプロパティ]** の順に選択します。 **ソリューション エクスプローラー** でプロジェクト ノードを右クリックし、 **[プロパティ]** をクリックすることもできます。  
  
2.  Visual Basic プロジェクトの場合は、 **[コンパイル]** タブを選択します。Visual C# プロジェクトの場合は、 **[ビルド]** タブを選択します。C++ プロジェクトまたは JavaScript プロジェクトの場合は、 **[全般]** タブを選択します。  
  
3.  上部にある構成のドロップダウンで、出力ファイルの場所を変更する構成を選択します (デバッグ、リリース、またはすべて)。  
  
     出力パスのエントリを検索します (Visual Basic の場合は **[ビルド出力パス]** 、Visual C++ の場合は **[出力ディレクトリ]** 、JavaScript と C# の場合は **[出力パス]** )。 プロジェクト ディレクトリを基準として相対的に新しいビルド出力ディレクトリを指定します。  
  
> [!NOTE]
>  セットアップ プロジェクトの **[出力ファイル名]** ボックスは、プロジェクト ファイルの場所ではなく、Setup.exe ファイルの場所のみを変更します。 詳細については、「 **配置プロジェクトの [プロパティ ページ] ダイアログ ボックス ([構成プロパティ] - [ビルド])**」を参照してください。  
  
## <a name="see-also"></a>「  
 [[ビルド] ページ (プロジェクト デザイナー) (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [[全般] プロパティ ページ (プロジェクト)](http://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45)   
 [コードのコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)
