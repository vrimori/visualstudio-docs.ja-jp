---
title: "プロジェクトのコンテキスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d74d804f65338edb589e63dde111e2ec1a4b5c6f
ms.lasthandoff: 02/22/2017

---
# <a name="project-context"></a>プロジェクトのコンテキスト
ユーザーを追加またはプロジェクトとプロジェクト アイテムが連携する、ときに、IDE、プロジェクトのコンテキストの概念を使用して、さまざまな操作を実行する必要がありますかを決定します。  
  
 ファイルを選択して、ユーザーが明示的を作成する標準的なプロジェクトのオブジェクトは、通常、**新しいプロジェクト**コマンドまたはを選択して使用できるように、**プロジェクトを開く**コマンドを**ファイル**メニュー。 このような場合は、ファイルが作成され、プロジェクトのコンテキストで開かれているし、プロジェクトの種類がドキュメントを編集するコンテキストを定義します。  
  
 いくつかのプロジェクトでは、非常に豊富なコンテキストを提供します。 たとえば、プロジェクトは、プロジェクト スコープ、プログラムの名前空間またはデータ バインド用にプロジェクト スコープのデータベース接続を管理します。 ユーザーは、ソリューション エクスプ ローラーに表示されるプロジェクト アイテムなどの特定のプロジェクト オブジェクトを使用して直接、ファイルやデータベース接続を開くことができます多くの場合。  
  
 それ以外の時間、プロジェクトのコンテキスト項目は、明示的に指定されていません。 など、コンテキスト アイテムを利用できないユーザーを選択して、ファイルを開いたとき、**既存ファイルを開く**コマンドを**ファイル** メニューの ファイル、またはユーザーがクリックすると、デバッガーが動作するとき、**ファイル内の検索**コマンドを**検索し、置換** ダイアログ ボックス。 これらの状況では、IDE の呼び出しを処理する<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>ドキュメントを開くための最適なプロジェクトを見つけ出すプロセスを管理する</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの優先順位](../../extensibility/internals/project-priority.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)
