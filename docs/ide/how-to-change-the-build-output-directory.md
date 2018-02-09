---
title: "方法 : ビルド出力ディレクトリを変更する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 14aad8b82a3757fecb1d449a671fc07c2582bb5f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-change-the-build-output-directory"></a>方法 : ビルド出力ディレクトリを変更する
プロジェクトによって生成された (デバッグ、リリース、またはその両方の) 構成ごとに出力の場所を指定できます。  
  
> [!NOTE]
>  **セットアップ** プロジェクトがある場合は、この記事の最後にあるメモを参照してください。  
  
## <a name="changing-the-build-output-directory"></a>ビルド出力ディレクトリの変更  
  
#### <a name="to-change-the-build-output-directory"></a>ビルド出力ディレクトリを変更するには  
  
1.  メニュー バーで、 **[プロジェクト]**、[ *Appname* **のプロパティ]**の順に選択します。 **ソリューション エクスプローラー** でプロジェクト ノードを右クリックし、 **[プロパティ]**をクリックすることもできます。  
  
2.  Visual Basic プロジェクトの場合は、 **[コンパイル]** タブを選択します。C# プロジェクトの場合は、**[ビルド]** タブを選択します。C++ プロジェクトまたは JavaScript プロジェクトの場合は、 **[全般]** タブを選択します。  
  
3.  上部にある構成のドロップダウンで、出力ファイルの場所を変更する構成を選択します (デバッグ、リリース、またはすべて)。  
  
     出力パスのエントリを検索します (Visual Basic の場合は**[ビルド出力パス]** 、Visual C++ の場合は **[出力ディレクトリ]** 、JavaScript と C# の場合は **[出力パス]** )。 プロジェクト ディレクトリを基準として相対的に新しいビルド出力ディレクトリを指定します。  
  
> [!NOTE]
>  セットアップ プロジェクトの **[出力ファイル名]** ボックスは、プロジェクト ファイルの場所ではなく、Setup.exe ファイルの場所のみを変更します。 詳細については、「 **配置プロジェクトの [プロパティ ページ] ダイアログ ボックス ([構成プロパティ] - [ビルド])**」を参照してください。  
  
## <a name="see-also"></a>参照  
 [[ビルド] ページ (プロジェクト デザイナー) (C#)](../ide/reference/build-page-project-designer-csharp.md)   
 [[全般] プロパティ ページ (プロジェクト)](/cpp/ide/general-property-page-project)   
 [コードのコンパイルとビルド](../ide/compiling-and-building-in-visual-studio.md)