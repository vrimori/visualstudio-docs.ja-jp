---
title: 使用可能なソースがありません |Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 671593cf19eab22d1b7e233481ee4004ca8ed8ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925100"
---
# <a name="no-source-available"></a>使用できるソースはありません
表示しようとしているコードのソース コードがプロジェクトに含まれていません。 原因として、**[呼び出し履歴]** ウィンドウまたは **[スレッド]** ウィンドウで、ソース コードのないモジュールをダブルクリックしたことが考えられます。 デバッグは継続できますが、ソース ウィンドウを使ってブレークポイントを設定したり、この場所で他のアクションを実行したりすることはできません。 ブレークポイントを設定する必要があるときは、代わりに **[逆アセンブリ]** ウィンドウを使用します。  
  
 [ソリューション  プロパティ ページ] で、デバッガーがソース ファイルを検索するディレクトリを変更したり、選択されたソース ファイルをデバッガーが無視したりするように設定できます。 参照してください[デバッグ ソース ファイル、一般的なプロパティは、ソリューション プロパティ ページ ダイアログ ボックス](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)します。  
  
 **[参照してソースを検索]**  
 このリンクをクリックすると、参照してソース コードを検索できるダイアログ ボックスが開きます。  
  
 **[逆アセンブルの表示]**  
 **[逆アセンブル]** ウィンドウを起動します。  
  
 **[見つからないソース ファイルには常に逆アセンブルを表示する]**  
 このオプションをオンにすると、利用できるソースがない場合に **[逆アセンブル] ウィンドウ**が自動的に表示されます。 この設定は、**[オプション]** ダイアログ ボックス、**[デバッグ]** カテゴリ、**[全般]** ページで、**[ソースがない場合は逆アセンブルの表示]** をオンまたはオフにすることによっても変更できます。  
  
## <a name="see-also"></a>「  
 [[デバッグ ソース ファイル] ([ソリューション プロパティ ページ] ダイアログ ボックス - [共通プロパティ])](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [シンボル (.pdb) とソース ファイルの指定](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (SOS デバッガー拡張)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)