---
title: 使用可能なソースがありません |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aae4b2428470e3e33477cfdb36699c2c1da20c1f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479742"
---
# <a name="no-source-available"></a>使用できるソースはありません
表示しようとしているコードのソース コードがプロジェクトに含まれていません。 一般的な原因が内にソース コードがないモジュールをダブルクリックすると、**呼び出し履歴 ウィンドウ**または**スレッド ウィンドウ**します。 デバッグは継続できますが、ソース ウィンドウを使ってブレークポイントを設定したり、この場所で他のアクションを実行したりすることはできません。 ブレークポイントを設定する必要がある場合、**逆アセンブル ウィンドウ**代わりにします。  
  
 [ソリューション  プロパティ ページ] で、デバッガーがソース ファイルを検索するディレクトリを変更したり、選択されたソース ファイルをデバッガーが無視したりするように設定できます。 参照してください[ソース ファイル、一般的なプロパティは、ソリューション プロパティ ページ ダイアログ ボックスをデバッグ](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)です。  
  
 **ソース コードを検索するには、[参照]**  
 このリンクをクリックすると、参照してソース コードを検索できるダイアログ ボックスが開きます。  
  
 **逆アセンブルを表示します。**  
 起動、**逆アセンブル ウィンドウ**します。  
  
 **常に逆アセンブル見つからないソース ファイルを表示します。**  
 表示するには、このオプションを選択して、**逆アセンブル ウィンドウ**自動的にソースが使用できない場合。 この設定を変更することも、**オプション**ダイアログ ボックスで、**デバッグ**カテゴリ、**全般** ページで、オンまたはオフにして**逆アセンブルを表示する場合ソースが利用できない**です。  
  
## <a name="see-also"></a>関連項目  
 [ソース ファイル、一般的なプロパティは、ソリューション プロパティ ページ ダイアログ ボックスをデバッグします。](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [シンボル (.pdb) を指定して、ソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (SOS デバッガー拡張)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)