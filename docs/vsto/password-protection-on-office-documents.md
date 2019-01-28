---
title: Office ドキュメントのパスワード保護
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 062196206d881ebb5a10f4bd7b14d892dbbbe0e9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872210"
---
# <a name="password-protection-on-office-documents"></a>Office ドキュメントのパスワード保護
  パスワードを知らない人によって開けませんように、Microsoft Office Word 文書と Microsoft Office Excel ブックにパスワードを設定することになります。 このオプションの名前は **[パスワード]** します。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 既存の文書やブックを使用してドキュメント レベルのプロジェクトを作成する **[パスワード]** を有効にします。 Visual Studio での動作が Word および Excel のドキュメントを異なる **[パスワード]** を有効にします。  
  
 有効化について **[パスワード]**、Word または Excel のヘルプを参照してください。  
  
## <a name="behavior-of-excel-and-word"></a>Excel および Word の動作  
 Visual Studio で Excel ブックを開くたびに **[パスワード]** が有効な入力を求められたら、パスワード。 ソリューションをビルドするときに促されます、パスワードをもう一度、ビルド中に、ドキュメントが開かれているためです。  
  
 初めてが Visual Studio で Word 文書を開く **[パスワード]** 有効にすると、Word が表示されたら、パスワードの。 正常にパスワードを入力した後 **[パスワード]** ドキュメントから削除されますドキュメントを開いて、パスワードが不要になったとします。 場合は、ソリューション内、ドキュメントを要求する前にパスワードを要求するのには開くことが、有効にする必要があります **[パスワード]** 最終的なビルドの後に、ソリューションをデプロイする前にします。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [方法: 制限されたアクセス許可を持つドキュメントの背後で実行するコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)  
