---
title: '[フォントおよび色] ノード プロパティ ([オプション] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18524cb3b27a05763187b9d5567d127af39c25d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539191"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>[フォントおよび色] ノード プロパティ ([オプション] ページ)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[オプション ページで、フォントおよび色 ノード プロパティ](https://docs.microsoft.com/visualstudio/ide/reference/options-page-fonts-and-colors-node-properties)します。  
  
  
このドキュメントでは、**[オプション]** ダイアログ ボックスの **[環境]** カテゴリの **[フォントと色]** に表示されるように登録されているツール ウィンドウのフォントと色のプロパティについて説明します。 ここで説明するプロパティを使用することにより、色を設定できる項目のグループの動的な特性がサポートされます。このグループは、VSPackages がインストールまたはアンインストールされる場合に変化させることができます。  
  
 次のセクションでは、登録されているウィンドウの種類の例、および各ウィンドウで使用できるプロパティを示します。  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>テキスト エディター、プリンターまたはダイアログとツール ウィンドウ  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 - または -  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 - または -  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|プロパティ項目名|[値]|説明|  
|------------------------|-----------|-----------------|  
|FontFamily|Get/Set (String)|使用するフォント名 ("MS P ゴシック" など)。|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|<xref:EnvDTE.vsFontCharSet> の値。ヘブライ語やロシア語など、使用する文字セットの種類を指定します。|  
|FontSize|Get/Set (Short)|使用するフォントのサイズ (ポイント単位)。 例: 10 や 12 など。|  
  
## <a name="see-also"></a>関連項目  
 [オプション設定の制御](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [オプション ページにあるプロパティ項目名の確認](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [[環境] ノード プロパティ ([オプション] ページ)](../../ide/reference/options-page-environment-node-properties.md)   
 [[テキスト エディター] ノード プロパティ ([オプション] ページ)](../../ide/reference/options-page-text-editor-node-properties.md)



