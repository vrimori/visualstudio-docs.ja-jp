---
title: "The project &lt;name&gt; must be converted to the current project format. (プロジェクト &lt;name&gt; を現在のプロジェクト形式に変換する必要があります。) | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The project &lt;name&gt; must be converted to the current project format. (プロジェクト &lt;name&gt; を現在のプロジェクト形式に変換する必要があります。)
以前のバージョンの Visual Studio で作成されたプロジェクトを開きました。 プロジェクト ファイルを現在の形式に変換しないと、コンピューターにインストールされているバージョンの Visual Studio でプロジェクトを開いたり編集したりすることはできません。 このプロジェクトをすぐに変換するかどうかを選択できます。 形式を変換したら、元に戻すことはできません。  
  
> [!CAUTION]
>  プロジェクトがソース コード管理されていて、変換後に再びチェックインする場合は、そのプロジェクトを共有しているソリューションが他にないかどうかを先に確認してください。 新しく変換したプロジェクトがまだ変換されていない他のソリューションで使用されている場合、チェックインしないでください。 チェックインすると、そのプロジェクトを使用している他のソリューション内の依存関係が壊れて、正しく開いたりビルドしたりできなくなります。  
  
 変換する前にプロジェクト ファイルのバックアップ コピーを作成しておくと安心です。  
  
> [!NOTE]
>  プロジェクトの種類によっては \(Visual C\+\+ プロジェクトなど\)、変換することで、変換前のファイルが .old という拡張子でプロジェクト ディレクトリに保存されます。  
  
 読み取り専用のプロジェクトは変換されません。 読み取り専用のプロジェクトを変換できるのは、編集のアクセス許可を持つユーザーだけです。 変換したソリューション内でプロジェクトを使用するには、そのプロジェクト ファイルを現在の形式に変換しておく必要があります。 いったんプロジェクトを変換すると、そのプロジェクトを含むソリューションを前のバージョンの Visual Studio で編集、ビルド、実行することはできません。  
  
### 対処方法  
  
1.  **\[はい\]** または **\[いいえ\]** をクリックします。  
  
    -   **\[はい\]** \- プロジェクトが編集可能な場合は、コンピューターにインストールされているバージョンの Visual Studio が使用する形式に変換されます。 変換したプロジェクトがソース コード管理されている場合は、ローカル ドライブにチェックアウトされ、編集できるように開かれます。  
  
    -   **\[いいえ\]** \- プロジェクトは変換されません。ソース コード管理からチェックアウトされることも、開かれることもありません。  
  
 チームで開発している場合は、同じプロジェクトで作業するすべてのメンバーが同じバージョンの Visual Studio をローカル コンピューターにインストールしている必要があります。 プロジェクトにアクセスできなくなることがないように、定期的にチームと連絡を取ってください。  
  
## 参照  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/ja-jp/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Visual Studio でのアプリケーションのビルド](../ide/compiling-and-building-in-visual-studio.md)