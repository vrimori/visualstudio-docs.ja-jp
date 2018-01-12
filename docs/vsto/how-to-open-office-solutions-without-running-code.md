---
title: "方法: コードを実行せずに Office ソリューションを開く |Microsoft ドキュメント"
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
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: bd7a401ab96cbb196d97b2e210b3ede0a624deb8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-open-office-solutions-without-running-code"></a>方法 : コードを実行せずに Office ソリューションを開く
  マネージ コード拡張機能で作成された Microsoft Office ソリューションでは、エンドユーザーの Office アプリケーションのセキュリティ設定が高に設定されている場合でも実行されます。 これは、.NET アセンブリのコードのセキュリティが Microsoft Office ではなく、Microsoft .NET Framework によって管理されているためです。  
  
 ただし、コードを実行せずに文書を開いたりする場合もあります。 たとえば、ドキュメントを開くときに実行されるコードは、内容を変わる可能性がありますが、文書の外観、コードの変更の前にそれを更新します。 または、他の人にある特定の情報を使用してドキュメントを送信して、コードを実行し、可能性のある内容が変更されないようにするには。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 開くには、文書またはブックをアセンブリ コードを実行しなくてもマネージ コード拡張機能を含むいくつかの方法はあります。  
  
### <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>SHIFT キーを使用してアセンブリをバイパスするには  
  
-   ドキュメントのブックを開き、**ファイル**を Word と Excel がドキュメントを開くときに、初期化イベントを発生させることを防ぐために、SHIFT キーを押しながらメニュー。  
  
    > [!NOTE]  
    >  ドキュメントまたはブックから開いた場合、**作業の開始**shift キーを押し、作業ウィンドウはコードをバイパスしていません。 また、shift キーを押しは防止しませんイベント ドキュメントが開かれた後に発生します。  
  
     このメソッドは、変更を加えるコードを実行していると、文書の変更がないドキュメントを開きたい場合に便利です。  
  
### <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>アセンブリをバイパスするには、名前の変更または削除するのには  
  
-   アセンブリが配置されているコンピューターに必要なアクセス許可があれば、名前を変更したり、ドキュメントまたはブックは、見つからないため、アセンブリを削除できます。 これは、結果、Office ドキュメントが開かれるたびに発生します。  
  
     複数のユーザーで、ソリューションを使用する場合、このメソッドは、それらのすべての実行から、ソリューションを防ぎます。 これはする、コードまたは参照先のサーバーで問題が検出され、すべてのユーザーから実行を停止する場合に役立ちます。  
  
## <a name="see-also"></a>参照  
 [Office ソリューションのセキュリティ保護](../vsto/securing-office-solutions.md)   
 [Office ソリューションの配置](../vsto/deploying-an-office-solution.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションにおけるアプリケーション マニフェストと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  