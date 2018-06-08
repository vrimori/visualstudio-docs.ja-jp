---
title: Office ソリューションの概要にあるローカル データベース ファイルを使用します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01e9dc3df93e1f721eba9ce3bcf65d4fb8bb1ca1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767583"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Office ソリューションの概要にあるローカル データベース ファイルを使用します。
  SQL Server Express などのデータベース ファイルを含めることができます (*.mdf*) ファイルまたは Microsoft Office Access (*.mdb*)、Office ソリューションでのファイルです。 これにより、一元化されたデータベースのメンテナンスができない場合は必要な 1 台のコンピューターのみで使用されているローカル インベントリ ソリューションの例にあるローカル データベースを維持するためにエンドユーザーことができます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>データベース ファイルをプロジェクトにインポートします。  
 プロジェクトにデータベース ファイルをインポートするには、使用、**データ ソース構成ウィザード**データベース ファイルに基づくデータ ソースを作成します。 ウィザードでは、データベース ファイルと型指定されたデータセットをプロジェクトに追加します。  
  
## <a name="deploy-the-database-file"></a>データベース ファイルを展開します。  
 **データ ソース構成ウィザード**相対パスを使用して、ローカル データベース ファイルへの接続を作成します。 これにより、ファイルの相対位置を保持している場合に、1 台のコンピューターからソリューションを別にコピーすることができます。  
  
 ソリューションをサーバーに配置し、各エンドユーザーにドキュメントを配布した場合も手動でデータベース ファイルを配布して、ドキュメントに対する相対位置が、インストールする必要があります。 つまり、そのユーザーも、データベース ファイルを移動しない限り、エンド ユーザーが自分のコンピューターで、新しい場所にドキュメントを移動できないことです。  
  
## <a name="local-database-files-and-caching-the-dataset"></a>ローカル データベース ファイルとデータセットのキャッシュ  
 Microsoft Office Excel および Microsoft Office Word のドキュメント レベルのソリューションでは、属性を持つデータセットのインスタンスをマークすることによって、ドキュメント内のデータセットをキャッシュできます<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>です。 追加すると、データベース ファイルをプロジェクトを使用して、**データ ソース構成ウィザード**、型指定されたデータセットが自動的にプロジェクトに追加します。 適用することはほとんどありません必要がある<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>、このデータセットにデータが既にローカル ユーザーのコンピューター上にあるためです。 詳細については、次を参照してください。[データ キャッシュ](../vsto/caching-data.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションでのコントロールにデータをバインドします。](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [方法: データベースからデータをドキュメントに読み込む](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [方法: ホスト コントロールからのデータでデータ ソースを更新](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Office ソリューションを配置します。](../vsto/deploying-an-office-solution.md)   
 [データのキャッシュ](../vsto/caching-data.md)  
  
  