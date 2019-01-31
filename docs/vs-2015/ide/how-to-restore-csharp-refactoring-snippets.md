---
title: '方法: C# リファクタリング スニペットを復元 |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ebd6b96a24b10601257d5eefc58014ef7058c9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782597"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>方法: C# リファクタリング スニペットを復元します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>「  
 [Visual C# のコード スニペット](../ide/visual-csharp-code-snippets.md)   
 [リファクタリング (C#)](../csharp-ide/refactoring-csharp.md)   
 [コード スニペット](../ide/code-snippets.md)
