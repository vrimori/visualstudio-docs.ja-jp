---
title: Office ソリューションを配置します。
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58e485384f80b2f0fdfc46a91caf305754a87301
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-an-office-solution"></a>Office ソリューションを配置します。
  ClickOnce または Windows インストーラーを使用して、Office ソリューションを配置できます。 ClickOnce を使用すると、ソリューションを配置および更新するために必要な手順の数を減らすことができます。 Windows インストーラーを使用する場合は、ユーザーがソリューションをインストールする際に、ソリューションをどのようにインストールするか、およびセットアップ プログラムがどのページを表示するかを制御できます。  
  
> [!NOTE]  
>  間での Office エクスペリエンスを拡張するソリューションの開発に関心のある[複数のプラットフォーム](https://dev.office.com/add-in-availability)しますか? チェック アウト新しい[Office アドイン モデル](https://dev.office.com/docs/add-ins/overview/office-add-ins)です。 Office アドインでは、VSTO アドインと、ソリューションと比較して、小さなフット プリントを持ち、ほぼすべての web プログラミング HTML5、JavaScript、CSS3、XML などのテクノロジを使用してそれらをビルドすることができます。  
  
## <a name="deploy-a-solution-by-using-clickonce"></a>ClickOnce を使用してソリューションを配置します。  
 ClickOnce を使用してソリューションを配置するときは、ユーザーがインストールして実行できる中央の場所にソリューションを発行します。 新しいセットアップ プログラムをユーザーに配布しなくても、ソリューションを更新できます。  この配置オプションの方が簡単ですが、ユーザーにカスタム設定ページを表示できません。 また、複数のユーザーがいるコンピューターでは、ソリューションを複数回インストールする必要があります。 参照してください[ClickOnce を使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-clickonce.md)です。  
  
## <a name="deploy-a-solution-by-using-windows-installer"></a>Windows インストーラーを使用してソリューションを配置します。  
 Windows インストーラーを使用してソリューションを配置するときは、ユーザーにセットアップ プログラムを配布し、ユーザーがそのプログラムを使用してソリューションをインストールします。 セットアップ プログラムを使用すると、現在のユーザーのみではなく、コンピューターのすべてのユーザーに同時にソリューションをインストールできます。 また、ユーザーがソリューションをインストールするときに表示されるオプションを、少し詳細に制御できます。 たとえば、使用許諾契約を表示したり、ユーザーがソリューションの特定のコンポーネントをインストールできるようにしたりすることができます。 ただし、ソリューションを更新する場合は、新しいセットアップ プログラムを配布する必要があります。 参照してください[Windows インストーラーを使用して Office ソリューションを配置](../vsto/deploying-an-office-solution-by-using-windows-installer.md)です。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [ClickOnce を使用して Office ソリューションを配置します。](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Windows インストーラーを使用して Office ソリューションを配置します。](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Office ソリューションの配置をトラブルシューティングします。](../vsto/troubleshooting-office-solution-deployment.md)  
  
  