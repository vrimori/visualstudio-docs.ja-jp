---
title: "その他のファイル | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- builds [Visual Studio], miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], outside of containers
- files [Visual Studio], Miscellaneous Files folder
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 831d0f60c992324c81cb1366ac28b3e3f1b066ad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="miscellaneous-files"></a>その他のファイル
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のエディターでは、プロジェクトともソリューションとも関係のないファイルを操作できます。 ソリューションを開いているときに、ファイルをソリューションやプロジェクトに追加せずに開いて編集できます。 コンテナーとは関係なく操作されるファイルを "その他のファイル" と呼びます。 "その他のファイル" は、ソリューションやプロジェクトの外部にあり、ビルドには含まれません。また、ソース管理の対象になっているソリューションに含めることはできません。  
  
 ファイルをコンテナーとは関係なく開くと、さまざまな利点があります。 たとえば、プロジェクト ベースのソリューションの開発中に、ソリューションの開発には必要のないファイルを表示できます。 こうしたファイルの例としては、開発メモ (指示書)、データベース スキーマ、コード クリップなどがあります。 また、スタンドアロンのファイルも作成できます。  
  
 ![ソリューション プロジェクト](../../ide/reference/media/projects_solutions_misc.gif "Projects_Solutions_Misc")  
  
 ソリューション エクスプローラーで該当する表示オプションを有効にすると、[その他のファイル] フォルダーが表示されます。 [[ドキュメント] ([オプション] ダイアログ ボックス - [環境])](../../ide/reference/documents-environment-options-dialog-box.md) から、オプションを設定することができます。 "その他のファイル" を閉じた後も特定のソリューションやプロジェクトとの関連付けを維持するには、そのためのオプションを有効にする必要があります。  
  
 [その他のファイル] フォルダーは、ファイルをリンクとして表します。 このフォルダーはソリューションの一部ではありませんが、設定によっては、ソリューションを開いたときに、前回ソリューションを閉じたときに開いていた "その他のファイル" の一部またはすべてが再び開かれます。  
  
> [!NOTE]
>  一部のファイルは [その他のファイル] フォルダーに表示されません。これらは、.zip ファイルや .doc ファイルのような IDE では変更できないファイルです。 IDE は外部エディターでしか変更できないファイルは追跡しません。  
  
## <a name="commands-available-in-the-ide"></a>IDE で使用できるコマンド  
 メニュー、ツール バー、およびそれらに含まれるコマンドは、開いたファイルの形式によって変化します。 たとえば、テキスト ファイルを開くと、[テキスト エディター] ツール バーが表示されて、そのコマンドを使用できるようになります。 その後 XML スキーマ ファイルを開くと、[XML スキーマ] ツール バーが表示されます。 XML スキーマを編集している間は、[テキスト エディター] ツール バーのコマンド ([テキスト エディター] ツール バー自体) は使用できなくなります。 このとき、XML スキーマがアクティブなウィンドウであるため、現在の選択コンテキストはこの XML スキーマにあります。 プロジェクト ファイルから "その他のファイル" に切り替えると、プロジェクト関連のコマンドはすべて表示されなくなり、そのファイルに直接関連するコマンドだけが表示されます。  
  
## <a name="folder-display-options"></a>フォルダー表示オプション  
 [その他のファイル] フォルダーの表示オプションを設定して、"その他のファイル" を一度も開いていない場合でも、このフォルダーを表示できます。 ソリューション ファイルは、"その他のファイル" の一覧を永久に管理するわけではありません。 ソリューション ファイルでは、オプションの機能を使用して、MRU ファイル リスト (最近使ったファイルの一覧) をユーザー別に保存できます。  
  
## <a name="see-also"></a>関連項目  
 [ソリューションおよびプロジェクト](../../ide/solutions-and-projects-in-visual-studio.md)   
 [[ドキュメント] ([オプション] ダイアログ ボックス - [環境])](../../ide/reference/documents-environment-options-dialog-box.md)