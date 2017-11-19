---
title: "ソース ファイル、一般的なプロパティは、ソリューション プロパティ ページ ダイアログ ボックスのデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96ca9ef63a3823b942a6d7a160c31473f5db8962
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>[デバッグ ソース ファイル] ([ソリューション プロパティ ページ] ダイアログ ボックス - [共通プロパティ])
このプロパティ ページでは、ソリューションのデバッグ時にデバッガーによってソース ファイルが検索される場所を指定します。  
  
 アクセスする、**デバッグ ソース ファイル**プロパティ ページで、ソリューション内で右クリック**ソリューション エクスプ ローラー**選択**プロパティ**ショートカット メニューからです。 展開、**共通プロパティ**フォルダー、およびをクリックして、**デバッグ ソース ファイル**ページ。  
  
 **ソース コードを含んでいるディレクトリ**  
 ソリューションのデバッグ時に、デバッガーによってソース ファイルが検索されるディレクトリの一覧が表示されます。 指定されたディレクトリのサブディレクトリも検索されます。  
  
 **これらのソース ファイルを探さない**  
 デバッガーによる読み取りから除外するファイルの名前を入力できます。 デバッガーは、上で指定したディレクトリのいずれかでこれらのファイルを見つけた場合、それを無視します。 場合、**ソースの検索** ダイアログ ボックスが表示されたらをデバッグしてをクリックしたときに**キャンセル**、探していたファイルがこの一覧に追加を取得できるように、デバッガーはそのファイルの検索を続行できません。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのセキュリティ](../debugger/debugger-security.md)   
 [デバッガーの設定と準備](../debugger/debugger-settings-and-preparation.md)