---
title: "コマンドを開く] を使用してファイルを表示します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ファイルを開くコマンドをサポートするプロジェクトの種類"
  - "ファイルを開くコマンド"
  - "永続化ストアを開くコマンドをサポートします。"
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# コマンドを開く] を使用してファイルを表示します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクトは ENT0ENT \[出力\] ダイアログ ボックスを表示するにはIDE を呼び出すことができます。  この要求はユーザーが標準エディターを選択できるファイルを開くように求められます。  次の手順ではこのプロセスについて説明します。  
  
1.  プロジェクトは `OSEOpenDocEditor` のパラメーターに OSE\_UseOpenWithDialog の値を指定する <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> を呼び出します。  
  
2.  ドキュメントのファイル名拡張子に基づいてレジストリ エディターで示されている任意指定されたドキュメントを開くことが確認しENT0ENT \[出力\] ダイアログ ボックスのこの情報が表示されます。  
  
    > [!NOTE]
    >  \[入力\] ENT0ENT ダイアログ ボックスに含める必要のある基本的なエディターのプロジェクトは該当する各エディターのエディターのファクトリを登録する必要があります。  基本的なエディターが <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> のメソッドの実装に適用されるプロジェクトの特定の型とともにのみ機能します。  IDE のコア バイナリ エディターとテキスト エディターの組み込みエディターのファクトリがあります。  IDE ではそれぞれの登録された Windows のファイルの関連付けの代わりにエディターのファクトリのインスタンスを作成します。  このようなファイルの例はMicrosoft Word です。  
  
3.  ユーザーが \[ENT0ENT\] ダイアログ ボックスから項目を選択するとIDE では <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> のメソッドを呼び出してドキュメントを開きます。  詳細については、「[方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)」を参照してください。  
  
## 参照  
 [開く、プロジェクト項目を保存します。](../../extensibility/internals/opening-and-saving-project-items.md)   
 [ファイルを開くコマンドを使用してファイルを表示します。](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)