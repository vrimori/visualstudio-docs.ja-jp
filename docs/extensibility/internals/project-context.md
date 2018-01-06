---
title: "プロジェクトのコンテキスト |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 99f073e7f27fc98c1c751ae8153adfeea0018e2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="project-context"></a>プロジェクトのコンテキスト
ユーザーを追加またはプロジェクトとプロジェクト項目では、IDE、プロジェクトのコンテキストの概念を使用して、さまざまな操作を実行する必要がありますを決定します。  
  
 通常、ファイルは、標準プロジェクト オブジェクトを選択すると、ユーザーが明示的を作成する、**新しいプロジェクト**コマンドまたはを選択して使用できるように、**プロジェクトを開く**コマンドを**ファイル**メニュー。 このような場合は、ファイルが作成され、プロジェクトのコンテキストで開かれているし、プロジェクトの種類がドキュメントを編集するためのコンテキストを定義します。  
  
 いくつかのプロジェクトでは、非常に豊富なコンテキストを提供します。 たとえば、プロジェクトは、プロジェクト スコープ、プログラムの名前空間またはデータ バインディングにプロジェクト スコープのデータベース接続を管理します。 ユーザーは、ソリューション エクスプ ローラーで表示されるプロジェクト アイテムなどの特定のプロジェクト オブジェクトを使用して直接、ファイルやデータベース接続を開くことができます頻繁にします。  
  
 他のタイミングで項目のプロジェクトのコンテキストが明示的に指定されていません。 たとえば、項目のコンテキストは を選択して、ファイルを開くとき、**既存ファイルを開く**コマンドを**ファイル**メニュー、ファイル、または、ユーザーがクリックしたときに、デバッガーが動作するときに、**ファイル内の検索**コマンドを**検索し、置換** ダイアログ ボックス。 これらの状況では、IDE の呼び出しを処理するために<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>を最適なプロジェクトを開くには、ドキュメントを検索するプロセスを管理します。  
  
## <a name="see-also"></a>参照  
 [プロジェクトの優先度](../../extensibility/internals/project-priority.md)   
 [プロジェクト テンプレートとプロジェクト項目テンプレートの追加](../../extensibility/internals/adding-project-and-project-item-templates.md)