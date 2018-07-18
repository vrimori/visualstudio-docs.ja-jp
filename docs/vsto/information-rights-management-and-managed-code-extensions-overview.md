---
title: Information rights management とマネージ コード拡張機能の概要
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263762"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Information rights management とマネージ コード拡張機能の概要
  Microsoft Office Word および Microsoft Office Excel は、Information Rights Management (IRM)、承認されていないユーザーを表示したり、機密情報を変更することを防止するのに役立つ機能を提供します。 詳細については、Information Rights Management のしくみ、特定の Office アプリケーションのヘルプを参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>制限されたアクセス許可を持つドキュメントの背後にあるコードを実行します。  
 場合は、ソリューションには、ドキュメントまたは既定では、IRM を使用するブックが含まれる、Word および Excel できないことを実行するためのコード。 ドキュメントの作成者であるか、フル コントロール アクセス権がある場合は、ソリューションが動作するように既定値を変更できます。 詳細については、次を参照してください。[する方法: コードのアクセス許可の制限をドキュメントの背後にある実行許可](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)です。  
  
 IRM の使用を防止する<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument>を取得またはドキュメントにキャッシュされているデータを操作します。  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>エンドユーザーはマネージ コード拡張機能を使用するドキュメントへのアクセス許可を制限します。  
 IRM を使用すると、アクセス許可を制限して、ソリューション内の文書またはブックにフル コントロール アクセス権を持つユーザーことができます。 たとえば、会計部門に属するユーザーは、データベースからデータを含むワークシートを自動的に設定するソリューションを使用して、そのユーザー場合は自分の部門内のユーザーにのみアクセスの変更と他のユーザーへの読み取りアクセスを許可します。 ユーザーは、アクセス許可の制限を追加するときに既定では、ワークシートの背後にあるコードを実行できないし、ワークシートは、データでは設定されません。  
  
 オブジェクト モデルへのプログラムによるアクセスを許可する既定のアクセス許可の設定を変更すると、問題を解決するには、文書またはブックにフル コントロール アクセス権を持つユーザーが必要があります。 詳細については、次を参照してください。[する方法: コードのアクセス許可の制限をドキュメントの背後にある実行許可](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Office ドキュメントのパスワード保護](../vsto/password-protection-on-office-documents.md)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [Office ソリューションを配置します。](../vsto/deploying-an-office-solution.md)   
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)  
  
  