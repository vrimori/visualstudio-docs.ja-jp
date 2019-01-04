---
title: Visual Studio の比較で VBA および Office ソリューション
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA code, managed code extensions
- managed code extensions [Office development in Visual Studio], VBA compared to
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09c5fdeb37fa09595cdfda99aba06b9546c5f696
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820084"
---
# <a name="vba-and-office-solutions-in-visual-studio-compared"></a>Visual Studio の比較で VBA および Office ソリューション
  Microsoft Visual Basic for Applications (VBA) は、Office アプリケーションと密接に連携されているアンマネージ コードを使用しています。 Visual Studio を使用して作成した Microsoft Office プロジェクトでは、.NET Framework および Visual Studio デザイン ツールを利用できます。  
  
 Visual Studio を使用して作成できる Office ソリューションの種類については、次を参照してください。 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)します。  
  
## <a name="comparison"></a>条件式  
 Visual Studio での VBA ソリューションと Office ソリューションの基本的な比較を次の表に示します。  
  
|VBA ソリューション|Visual Studio の Office ソリューション|  
|-------------------|---------------------------------------|  
|特定のドキュメントに接続され、永続化するコードを使用します。|(ドキュメント レベルのカスタマイズ)、ドキュメントとは別に格納されているコードを使用または (VSTO アドイン) のアプリケーションによって読み込まれるアセンブリ。|  
|Office オブジェクト モデルと VBA API に使用できます。|Office オブジェクト モデルと [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] API の両方にアクセスできます。|  
|マクロの記録、開発者の作業の簡略化のために設計されています。|セキュリティ、コード保守の簡略化、すべての Visual Studio 統合開発環境 (IDE) の利用のために設計されています。|  
|Office アプリケーションとの緊密な統合の恩恵をソリューションに適しています。|Visual Studio と [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]のすべてのリソースを利用するソリューションに適しています。|  
|企業の場合は、特にセキュリティと開発の面で制限事項があります。|企業で使用するために設計されています。|  
  
 一部の作業は、VBA を使用する方が簡単にすばやく実行できます。 特に、次の場合は、引き続き VBA を使用することができます。  
  
-   カスタムのワークシート関数。  
  
-   マクロの記録。  
  
## <a name="combine-vba-solutions-and-office-solutions-created-by-using-visual-studio"></a>VBA ソリューションと Visual Studio を使用して作成された Office ソリューションを組み合わせる  
 Visual Studio を使用して作成された Office ソリューションから VBA コードを呼び出すことができます。また、VBA から Visual Studio を使用して作成された Office ソリューションのコードを呼び出すこともできます。 具体的な手法は、Office ソリューションが VSTO アドインか、ドキュメントレベルのカスタマイズかどうかによって異なります。 詳細については、次を参照してください。[他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)と[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Office ソリューション開発の概要&#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [他の Office ソリューションから VSTO アドイン内のコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [VBA とドキュメント レベルのカスタマイズを結合します。](../vsto/combining-vba-and-document-level-customizations.md)   
 [ドキュメント レベルのカスタマイズのアーキテクチャ](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [開始&#40;Visual Studio での Office 開発&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
