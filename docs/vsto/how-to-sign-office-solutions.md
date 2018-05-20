---
title: '方法: Office ソリューションの署名'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d5fa4a837de66a39502e2c9e2d8466f3998acc4d
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-sign-office-solutions"></a>方法: Office ソリューションの署名
  ソリューションに署名する場合は、証拠として、証明書を使用してソリューションに信頼を付与できます。 複数のソリューションに対して、同じ証明書を使用してによる追加のセキュリティ ポリシー更新のないすべてのソリューションが信頼されます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 アプリケーションを手動で編集すると、配置が、マニフェストの生成および編集ツールを使用してマニフェスト (*mage.exe*と*mageui.exe*)、使用できるようにマニフェストに再署名する必要があります。 詳細については、次を参照してください。[する方法: アプリケーション マニフェストと配置マニフェストに再署名](/visualstudio/deployment/how-to-re-sign-application-and-deployment-manifests)です。  
  
## <a name="sign-by-using-a-certificate"></a>証明書を使用して署名します。  
 証明書は、一意のキーとソリューションの発行元の id を含むファイルです。 証明機関から証明書を購入または独自の証明書を作成し、証明機関の署名があることがことができます。  
  
 Visual Studio は、Office ソリューションのデバッグを有効に一時的な証明書で署名します。 証拠として配置されるソリューションで一時的な証明書を使用する必要がありますされません。  
  
### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>証明書を使用して Office ソリューションを署名するには  
  
1.  **プロジェクト** メニューのをクリックして * SolutionName ***プロパティ**です。  
  
2.  **[署名]** タブをクリックします。  
  
3.  選択**ClickOnce マニフェストに署名**です。  
  
4.  クリックして、証明書を探します**ストアから選択**または**ファイルから選択**し、証明書に移動します。  
  
5.  適切な証明書を使用していることを確認する をクリックして**詳細**証明書情報を表示します。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [Office ソリューションに信頼を付与](../vsto/granting-trust-to-office-solutions.md)   
 [[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)  
  
  