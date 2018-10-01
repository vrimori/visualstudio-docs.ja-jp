---
title: '[参照設定] ページ (プロジェクト デザイナー) (Visual Basic) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5e89b77749b331665869393b2b3cf7e520d3371
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539868"
---
# <a name="references-page-project-designer-visual-basic"></a>[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[参照設定 ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)します。  
  
  
**[プロジェクト デザイナー]** の **[参照]** ページを利用し、プロジェクトの参照、Web 参照、インポートした名前空間を管理します。 プロジェクトには、COM コンポーネント、XML Web サービス、.NET Framework クラス ライブラリまたはアセンブリ、その他のクラス ライブラリの参照を含めることができます。 参照の使用方法については、「[プロジェクト内の参照の管理](../../ide/managing-references-in-a-project.md)」を参照してください。  
  
 **[参照]** ページにアクセスするには、**ソリューション エクスプローラー**のプロジェクト ノード (**[ソリューション]** ノードではありません) を選択します。 その後、メニュー バーで **[プロジェクト]**、**[プロパティ]** の順に選択します。 プロジェクト デザイナーが表示されたら、**[参照]** タブをクリックします。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 次のオプションを使用すると、プロジェクトの参照やインポートした名前空間を選択または削除できます。  
  
 **[未使用の参照]**  
 このボタンをクリックすると、**[未使用の参照]** ダイアログ ボックスにアクセスします。  
  
 **[未使用の参照]** ダイアログ ボックスでは、プロジェクトに含まれているが、実際にはコードで使用されていない参照を削除できます。 このボックスに含まれるグリッドには、**参照名**、**パス**、プロジェクトで使用されていない名前空間参照に関するその他の情報が一覧表示されています。 このグリッドで、プロジェクトから削除する名前空間参照を選択し、**[削除]** をクリックします。  
  
 **[参照パス]**  
 このボタンをクリックすると、**[参照パス]** ダイアログ ボックスにアクセスします。  
  
> [!NOTE]
>  プロジェクト システムでは、検出されたアセンブリ参照が解決されます。解決するとき、次の場所で次の順序で検索されます。  
>   
>  1.  プロジェクト フォルダー。 **[すべてのファイルを表示]** が有効になっていないとき、**ソリューション エクスプローラー**にプロジェクト フォルダー ファイルが表示されます。  
> 2.  **[参照パス]** ダイアログ ボックスに指定されているフォルダー。  
> 3.  **[参照の追加]** ダイアログ ボックスでファイルを表示するフォルダー。  
> 4.  プロジェクトの obj フォルダー。 (プロジェクトに COM 参照を追加するとき、1 つまたは複数のアセンブリをプロジェクトの obj フォルダーに追加できることがあります。)  
  
 **参照**  
 この一覧には、使用か未使用かを問わず、プロジェクトのすべての参照が表示されます。  
  
 **[追加]**  
 このボタンをクリックすると、参照または Web 参照が **[参照]** 一覧に追加されます。  
  
 [参照の追加] ダイアログ ボックスを利用してプロジェクトに参照を追加するには、**[参照]** を選択します。  
  
 [Web 参照の追加] ダイアログ ボックスを利用してプロジェクトに Web 参照を追加するには、**[Web 参照]** を選択します。  
  
 **削除**  
 **[参照]** 一覧で 1 つまたは複数の参照を選択し、このボタンをクリックして削除します。  
  
 **[Web 参照の更新]**  
 **[参照]** 一覧の Web 参照を選択し、このボタンをクリックして更新します。  
  
 **[インポートされた名前空間]**  
 このボックスに独自の名前空間を入力し、**[ユーザー インポートの追加]** をクリックし、名前空間一覧に追加します。  
  
 ユーザーがインポートした名前空間にエイリアスを作成できます。 これを行うには、*エイリアス*=*名前空間* の形式でエイリアスと名前空間を入力します。 これは、`Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http` のような、長い名前空間を使用する場合に便利です。  
  
 **[ユーザー インポートの追加]**  
 このボタンをクリックし、**[インポートされた名前空間]** ボックスに指定されている名前空間をインポートした名前空間の一覧に追加します。 このボタンは、指定の名前空間が一覧にまだない場合にのみ有効になります。  
  
 **[名前空間の一覧]**  
 この一覧には、利用可能なすべての名前空間が表示されます。 プロジェクトに含まれている名前空間のチェック ボックスが選択されます。  
  
 **[ユーザー インポートの更新]**  
 名前空間の一覧でユーザー指定の名前空間を選択し、**[インポートされた名前空間]** ボックスにその新しい名前を入力し、このボタンをクリックして新しい名前空間に変更します。 このボタンは、選択した名前空間が **[ユーザー インポートの追加]** ボタンを利用して一覧に追加した名前空間の場合にのみ表示されます。 追加できる項目:  
  
-   <xref:System.Math?displayProperty=fullName> など、クラスまたは名前空間。  
  
-   `VB=Microsoft.VisualBasic` など、エイリアスが付けられたインポート。  
  
-   `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">` など、XML 名前空間。  
  
## <a name="see-also"></a>関連項目  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [方法 : インポートした名前空間を追加または削除する (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)   
 [NIB: Web 参照 ダイアログ ボックスを追加します。](http://msdn.microsoft.com/en-us/bdf05776-c591-40af-bfd7-e1e2aa1e87b5)   
 [Imports ステートメント (XML 名前空間)](http://msdn.microsoft.com/library/1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4)



