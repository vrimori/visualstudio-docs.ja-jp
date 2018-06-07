---
title: Office ドキュメントのパスワード保護 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a278677b40f8da703c7f3287851c2f82fb95a21c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572713"
---
# <a name="password-protection-on-office-documents"></a>Office ドキュメントのパスワード保護
  パスワードを知らない人に開けませんできるように、Microsoft Office Word 文書と Microsoft Office Excel ブックでパスワードを設定することができます。 このオプションの名前は **[パスワード]** です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 既存のドキュメントおよびいるブックを使用してドキュメント レベルのプロジェクトを作成する **[パスワード]** 有効にします。 持つ Word および Excel のドキュメントの Visual Studio での動作が異なります **[パスワード]** 有効にします。  
  
 有効化については **[パスワード]**、Word または Excel でのヘルプを参照してください。  
  
## <a name="behavior-of-excel-and-word"></a>Excel および Word の動作  
 Visual Studio で Excel ブックを開くたびに **[パスワード]** が有効な入力を求められたら、パスワードです。 ソリューションをビルドするときに求められます、パスワードをもう一度、ビルド時にドキュメントが開かれているためです。  
  
 最初に開く、Word 文書が Visual Studio で **[パスワード]** 有効にすると、単語の入力を求め、パスワードです。 正常にパスワードを入力した後 **[パスワード]** ドキュメントから削除し、ドキュメントを開いて、パスワードは必要なくなった。 ソリューションでドキュメントをする場合は、前にパスワードを要求するように開くことができる、有効にする必要があります **[パスワード]** 最終的なビルドの後に、ソリューションを展開する前にします。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのソリューションでドキュメントの保護](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management とマネージ コード拡張機能の概要](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [方法: ドキュメントの背後にあるアクセス許可の制限を実行するコードを許可します。](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [設計および Office ソリューションを作成します。](../vsto/designing-and-creating-office-solutions.md)  
  
  