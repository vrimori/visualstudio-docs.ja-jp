---
title: "新しい項目の追加コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ef0373d148d386d0b725d74ea639f1b8b0719cc3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="add-new-item-command"></a>AddNewSolutionItem コマンド
新規ソリューションのアイテム (.htm、.css、.txt、フレームセットなど) を現在のソリューションに追加して、そのソリューションを開きます。  
  
## <a name="syntax"></a>構文  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 省略可能です。 ソリューションに追加する項目のパスとファイル名。  
  
## <a name="switches"></a>スイッチ  
 /t: `templatename`  
 省略可能です。 作成するファイルの種類を指定します。 テンプレート名が指定されていない場合は、既定でテキスト ファイルが作成されます。  
  
 /t:`templatename` 引数の構文は、**[新しいソリューション項目の追加]** ダイアログ ボックスの情報をミラー化します。 ファイルの種類が後に続く完全なカテゴリを入力する必要があります。その場合、カテゴリ名とファイルの種類を円記号 (`\`) で区切り、引用符で文字列全体を囲みます。  
  
 たとえば、新しいテキスト ファイルを作成する場合は、/t:`templatename` 引数に対して次のように入力します。  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 省略可能です。 ファイルが開かれるエディターの名前。 引数は指定されていても、エディター名がない場合、**[プログラムから開く]** ダイアログ ボックスが表示されます。  
  
 /e:`editorname` 引数の構文では、**[プログラムから開く] ダイアログ ボックス**に表示されるエディター名 (引用符で囲まれている) が使用されます。  
  
 たとえば、ソース コード エディターでスタイル シートを開く場合、/e:`editorname` 引数に対して次のように入力します。  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>例  
 この例では、現在のソリューションに、MyHTMLpg という新しいソリューション項目を追加します。  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)   
 [コマンド ウィンドウ](../../ide/reference/command-window.md)   
 [[検索/コマンド] ボックス](../../ide/find-command-box.md)   
 [Visual Studio コマンドのエイリアス](../../ide/reference/visual-studio-command-aliases.md)