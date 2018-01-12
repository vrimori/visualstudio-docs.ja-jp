---
title: "ドキュメントへの信頼の付与 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5c8cb7bc19c4668c9315c516430ffe8a8ff30ddc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="granting-trust-to-documents"></a>Granting Trust to Documents
  ドキュメント レベルのプロジェクトでは、証明書を使用したマニフェストへの署名や、信頼プロンプトのクリックなど、アプリケーション レベルのプロジェクトと同じセキュリティ要件が適用されます。 また、ドキュメントまたはブックは、信頼できる場所として指定されたディレクトリに置く必要があります。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>信頼できる場所  
 アプリケーションで[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]Office 2010 がセキュリティ センターのユーザーが信頼できる場所などのセキュリティとプライバシーの設定を構成できます。 Office ソリューションでは、ローカル コンピューターが信頼できる場所と見なされます。 ただし、ディレクトリの中には、リスクが高めであるために信頼できないものもあります (システム、各ユーザー、Internet Explorer 用の一時フォルダーなど)。  
  
 セキュリティ センターの詳細については、次を参照してください。[セキュリ ティー ポリシーと Office 2010 での設定](http://go.microsoft.com/fwlink/?LinkId=89202)です。 作成、管理、削除、および信頼できるフォルダーを構成する方法の詳細については、次を参照してください[2007 Office system で信頼できる場所および信頼できる発行元の設定を構成する](http://go.microsoft.com/fwlink/?LinkId=89203)と[作成、削除、または変更します。信頼できるファイルの場所の](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)します。  
  
## <a name="security-considerations-for-office-solutions"></a>Office ソリューションに固有のセキュリティに関する考慮事項  
 どのフォルダーを信頼できる場所に追加するかを検討するときには、以下のセキュリティ上の問題に留意する必要があります。  
  
-   ローカル フォルダーは安全性が高いと見なされ、暗黙的に信頼されます。  ファイル共有などのリモートの場所は、信頼できる場所として指定する必要があります。  
  
-   信頼できる場所にディレクトリを追加すると、Office ソリューションだけでなく VBA コードおよび ActiveX コードにも完全な信頼が付与されます。 そのため、ルート ディレクトリやマイ ドキュメント フォルダーは信頼できる場所として指定しないでください。  
  
-   ドキュメント自体は信頼できる場所を使用することによって信頼されますが、カスタマイズを信頼するためには追加のアクセス許可が必要です。 カスタマイズに完全な信頼を付与するには、証明書を使用したマニフェストへの署名、信頼プロンプトのクリック、Office ソリューションの Program Files ディレクトリへのインストールのいずれかを行います。  
  
-   ドキュメント レベルのソリューションのドキュメントまたはブックは、アセンブリと同じディレクトリ、または別のディレクトリに保存できます。 たとえば、ドキュメントを SharePoint サーバー上に置き、アセンブリをネットワーク ファイル共有に置くことも可能です。 詳細については、次を参照してください。[する方法: ClickOnce を使用して SharePoint サーバーにドキュメント レベルの Office ソリューションを発行](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)です。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションへの信頼の付与](../vsto/granting-trust-to-office-solutions.md)   
 [Office ソリューションのセキュリティのトラブルシューティング](../vsto/troubleshooting-office-solution-security.md)   
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)  
  
  