---
title: '方法 : C# リファクタリング スニペットを復元する | Microsoft Docs'
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
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13867274ace5582b25482868ddd3642426b1f295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537383"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>方法 : C# リファクタリング スニペットを復元する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 復元 c# リファクタリング スニペット](https://docs.microsoft.com/visualstudio/ide/how-to-restore-csharp-refactoring-snippets)します。  
  
C# リファクタリング操作は、次のディレクトリにあるコード スニペットに依存しています。  
  
 *インストール ディレクトリ*\Microsoft Visual Studio 14.0\VC#\Snippets\\*言語 ID*\Refactoring  
  
 この Refactoring ディレクトリまたはこのディレクトリ内のファイルを削除または破損すると、IDE では、C# リファクタリング操作が機能しない場合があります。 次の手順は、C# リファクタリング コード スニペットを復元する場合に役立ちます。  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>C# リファクタリング スニペットをコード スニペット マネージャーで使用できることを確認するには  
  
1.  **[ツール]** メニューの **[コード スニペット マネージャー]** を選びます。  
  
2.  **[コード スニペット マネージャー]** ダイアログ ボックスで、**[言語]** ボックスの一覧の **[Visual C#]** を選びます。  
  
     **[リファクタリング]** フォルダーがツリー ビューのフォルダーの一覧に表示されます。  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>コード スニペット マネージャーでリファクタリングの see コメントを復元するには  
  
1.  コード スニペット マネージャーのツリー ビューのフォルダーの一覧に **[リファクタリング]** フォルダーが表示されない場合は、次の手順を使って、リファクタリング スニペットをコード スニペット マネージャーに追加します。  
  
2.  **[ツール]** メニューの **[コード スニペット マネージャー]** を選びます。  
  
3.  **[コード スニペット マネージャー]** ダイアログ ボックスで、**[言語]** ボックスの一覧の **[Visual C#]** を選びます。  
  
4.  **[追加]** をクリックします。 **[コード スニペット ディレクトリ]** ダイアログ ボックスが表示されます。このダイアログ ボックスを使って、コード スニペット マネージャーに追加するディレクトリを検索および指定します。  
  
5.  次のディレクトリ パスにある **Refactoring** フォルダーに移動します。  
  
     *インストール ディレクトリ*\Microsoft Visual Studio 14.0\VC#\Snippets\\*言語 ID*\Refactoring  
  
     既定のインストールでは、実際のパスは次のようになります。  
  
     C:\Program Files\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring  
  
6.  **[コード スニペット ディレクトリ]** ダイアログ ボックスの **[開く]** をクリックし、コード スニペット マネージャーの **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [Visual C# のコード スニペット](../ide/visual-csharp-code-snippets.md)   
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)   
 [コード スニペット](../ide/code-snippets.md)



