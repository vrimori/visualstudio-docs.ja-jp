---
title: "方法: Office ソリューションの構成情報を設定 |Microsoft ドキュメント"
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6f604fa40a9816d5e46593bc50fcb91f82d13325
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>方法 : Office ソリューションの構成情報を設定する
  構成ファイルを使用して、Office ソリューションに固有の設定を構成することができます。 アセンブリ バインディング ポリシー、リモート処理オブジェクト、デバッグ、およびトレースの設定などの設定を指定することができます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>構成ファイルを Office プロジェクトに追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]**をクリックします。  
  
2.  **カテゴリ** ウィンドウで、をクリックして**全般**です。  
  
3.  **テンプレート**ペインで、**アプリケーション構成ファイル**です。  
  
4.  **名前**ボックスに、アセンブリ、.config 拡張子として同じ名前を入力します。たとえば、ExcelWorkbook1.dll という名前の Excel プロジェクト アセンブリの構成ファイルの名前は、ExcelWorkbook1.dll.config には。  
  
5.  **[追加]**をクリックします。  
  
6.  アプリケーション構成ファイル スキーマに従って、構成ファイルを作成します。 詳細については、次を参照してください。 [、.NET Framework の構成ファイル スキーマ](/dotnet/framework/configure-apps/file-schema/index)です。  
  
 Office プロジェクトで構成ファイルの使用に関する注意事項はありません。  
  
## <a name="see-also"></a>参照  
 [.NET Framework の構成ファイル スキーマ](/dotnet/framework/configure-apps/file-schema/index)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)  
  
  