---
title: '方法: プライマリ相互運用機能アセンブリをターゲットの Office アプリケーション'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 32ff157e3986836ac13472c4a9ed8a7b01f06e04
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>方法: プライマリ相互運用機能アセンブリをターゲットの Office アプリケーション
  新しい Office プロジェクトを作成すると、Visual Studio により、そのプロジェクトのビルドに必要な Microsoft Office プライマリ相互運用機能アセンブリ (PIA: Primary Interop Assembly) への参照が自動的に追加されます。 次の場合は、他の PIA への参照を追加する必要があります。  
  
-   プロジェクトで他の Microsoft Office アプリケーションの機能を使用する。 たとえば、Microsoft Office Word プロジェクトで Microsoft Office Excel の機能を使用することが必要になる場合があります。  
  
-   Microsoft Office Access など、Visual Studio に専用のプロジェクトがない Microsoft Office アプリケーションを自動化する。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>プライマリ相互運用機能アセンブリに参照を追加するには  
  
1.  Office プロジェクトを開きでプロジェクト名を選択**ソリューション エクスプ ローラー**です。  
  
2.  **[プロジェクト]** メニューの **[参照の追加]** をクリックします。  
  
3.  **Framework**  タブで、使用 PIA をでを選択、**コンポーネント名** ボックスの一覧です。 使用可能な Microsoft Office プライマリ相互運用機能アセンブリの詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
     場合プロジェクトの対象、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]またはそれ以降、**相互運用機能型の埋め込み**アセンブリ参照のプロパティに設定されて**True**既定です。 この設定を使用すると、ソリューションはエンド ユーザーのコンピューターに PIA を必要としません。 詳細については、次を参照してください。[デザインおよび Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)です。  
  
    > [!NOTE]  
    >  Office プロジェクトを使用して常に Office Pia への参照を追加、 **.NET**のタブ、**参照の追加**ダイアログではなく、 **COM**タブです。詳細については、次を参照してください。 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)です。  
  
4.  **[OK]** をクリックします。  
  
     アセンブリ名が表示されます、**参照**のフォルダー**ソリューション エクスプ ローラー**です。  
  
## <a name="see-also"></a>関連項目  
 [Office プライマリ相互運用機能アセンブリ](../vsto/office-primary-interop-assemblies.md)   
 [Office ソリューションでコードを記述します。](../vsto/writing-code-in-office-solutions.md)   
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [方法: Office プライマリ相互運用機能アセンブリ](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  