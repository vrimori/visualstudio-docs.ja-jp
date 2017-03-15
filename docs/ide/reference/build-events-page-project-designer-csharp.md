---
title: "[ビルド イベント] ページ (プロジェクト デザイナー) (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "ビルド イベント"
  - "プロジェクト デザイナー、[ビルド イベント] ページ"
  - "ビルド前のイベント"
  - "ビルド後のイベント"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# [ビルド イベント] ページ (プロジェクト デザイナー) (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**プロジェクト デザイナー**の **\[ビルド イベント\]** ページを使用すると、ビルド構成の手順を指定できます。  また、ビルド後の任意のイベントを実行する条件を指定することもできます。  詳細については、「[方法 : ビルド イベントを指定する \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)」および「[方法 : ビルド イベントを指定する \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)」を参照してください。  
  
## UIElement の一覧  
 **構成**  
 このコントロールは、このページでは編集できません。  このコントロールの詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
 **プラットフォーム**  
 このコントロールは、このページでは編集できません。  このコントロールの詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
 **ビルド前に実行するコマンド ライン**  
 ビルド開始前に実行する任意のコマンドを指定します。  長いコマンドを入力するには、**\[ビルド前の編集\]** をクリックして [\[ビルド前に実行するコマンド ライン\] \/ \[ビルド後に実行するコマンド ライン\] ダイアログ ボックス](../Topic/Pre-build%20Event-Post-build%20Event%20Command%20Line%20Dialog%20Box.md)を表示します。  
  
> [!NOTE]
>  ビルド前のイベントは、プロジェクトが最新の状態で、ビルドが発生しない場合には実行しません。  
  
 **ビルド後のイベント コマンド ライン**  
 ビルド終了後に実行する任意のコマンドを指定します。  長いコマンドを入力するには、**\[ビルド後の編集\]** をクリックして **\[ビルド後に実行するコマンド ライン\]** ダイアログ ボックスを表示します。  
  
> [!NOTE]
>  .bat ファイルを実行するすべてのビルド後コマンドの前に、`call` ステートメントを追加します。  たとえば、`call C:\MyFile.bat` または `call C:\MyFile.bat call C:\MyFile2.bat` です。  
  
 **ビルド後のコマンド ラインの実行条件**  
 次の表に示すように、実行するビルド後のイベントの条件を指定します。  
  
|オプション|結果|  
|-----------|--------|  
|**常時**|ビルド後のイベントは、ビルドが成功したかどうかに関係なく実行されます。|  
|**ビルドが成功したとき**|ビルド後のイベントは、ビルドが成功した場合に実行されます。  このため、ビルドが成功した場合は、最新のプロジェクトについてもイベントが実行されます。|  
|**\[ビルドがプロジェクト出力を更新したとき\]**|ビルド後のイベントは、コンパイラの出力ファイル \(.exe または .dll\) が以前のコンパイラの出力ファイルと異なる場合にだけ実行されます。  このため、ビルド後のイベントは、プロジェクトが最新の場合は実行されません。|  
  
## 参照  
 [方法 : ビルド イベントを指定する \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [方法 : ビルド イベントを指定する \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [プロジェクトのプロパティのリファレンス](../../ide/reference/project-properties-reference.md)   
 [Visual Studio でのアプリケーションのビルド](../../ide/compiling-and-building-in-visual-studio.md)