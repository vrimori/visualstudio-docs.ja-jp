---
title: ドキュメントに信頼を付与
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aba47e277b1c109bf4b0d03efb5694733f45760c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871885"
---
# <a name="grant-trust-to-documents"></a>ドキュメントに信頼を付与
  ドキュメント レベルのプロジェクトでは、証明書を使用したマニフェストへの署名や、信頼プロンプトのクリックなど、アプリケーション レベルのプロジェクトと同じセキュリティ要件が適用されます。 また、ドキュメントまたはブックは、信頼できる場所として指定されたディレクトリに置く必要があります。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>信頼できる場所  
 アプリケーションで[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]Office 2010 がセンターのユーザーが信頼できる場所などのセキュリティとプライバシーの設定を構成できます。 Office ソリューションでは、ローカル コンピューターが信頼できる場所と見なされます。 ただし、ディレクトリの中には、リスクが高めであるために信頼できないものもあります (システム、各ユーザー、Internet Explorer 用の一時フォルダーなど)。  
  
 セキュリティ センターの詳細については、次を参照してください。[セキュリティ ポリシーと Office 2010 で設定](http://go.microsoft.com/fwlink/?LinkId=89202)します。 作成、管理、削除、および信頼されているフォルダーを構成する方法の詳細については、次を参照してください[、2007 Office system で信頼できる場所および信頼された発行元の設定を構成する](http://go.microsoft.com/fwlink/?LinkId=89203)と[作成、削除、または変更します。ファイルの場所を信頼された](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)します。  
  
## <a name="security-considerations-for-office-solutions"></a>Office ソリューションのセキュリティに関する考慮事項  
 どのフォルダーを信頼できる場所に追加するかを検討するときには、以下のセキュリティ上の問題に留意する必要があります。  
  
-   ローカル フォルダーは安全性が高いと見なされ、暗黙的に信頼されます。  ファイル共有などのリモートの場所は、信頼できる場所として指定する必要があります。  
  
-   信頼できる場所にディレクトリを追加すると、Office ソリューションだけでなく VBA コードおよび ActiveX コードにも完全な信頼が付与されます。 このため、ルート ディレクトリと*My Documents*フォルダーを指定しない必要があります trusted とします。  
  
-   ドキュメント自体は信頼できる場所を使用することによって信頼されますが、カスタマイズを信頼するためには追加のアクセス許可が必要です。 証明書を使用したマニフェストの署名、信頼プロンプトの表示、またはに Office ソリューションのインストールを使用して、カスタマイズに完全な信頼を付与することができます、 *Program Files*ディレクトリ。  
  
-   ドキュメント レベルのソリューションのドキュメントまたはブックは、アセンブリと同じディレクトリ、または別のディレクトリに保存できます。 たとえば、ドキュメントを SharePoint サーバー上に置き、アセンブリをネットワーク ファイル共有に置くことも可能です。 詳細については、「[方法 :ClickOnce を使用して、ドキュメント レベルの Office ソリューションを SharePoint サーバーに発行](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューションに信頼を付与](../vsto/granting-trust-to-office-solutions.md)   
 [Office ソリューションのセキュリティをトラブルシューティングします。](../vsto/troubleshooting-office-solution-security.md)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)  
