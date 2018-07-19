---
title: '方法: コードを実行せず、Open Office ソリューション'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: f7ced7b38a4f32d96b397e7f9eebb1d40be03ae3
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254989"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>方法: コードを実行せず、Open Office ソリューション
  マネージ コード拡張機能で作成された Microsoft Office ソリューションでは、エンドユーザーの Office アプリケーションのセキュリティ設定が [高] に設定されている場合でも実行されます。 これは、.NET アセンブリのコードのセキュリティは、Microsoft Office ではなく、Microsoft .NET Framework によって管理されるためです。  
  
 ただし、コードを実行せず、ドキュメントを開きたい場合もあります。 たとえば、ドキュメントを開くときに実行されるコードが、内容に変わる可能性がありますが、ドキュメントのコードを変更する前に表示する方法を更新します。 だれかが特定の情報を使用してドキュメントを送信する場合や、コードを実行し、場合によって、内容を変更したくないです。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 ドキュメントまたはアセンブリのコードを実行しなくてもマネージ コード拡張機能を含むブックを開くのいくつかの方法はあります。  
  
## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift キーを使用して、アセンブリをバイパスするには  
  
-   ドキュメントおよびからブックを開く、**ファイル**メニューを押しながら、 **Shift** Word および Excel のドキュメントを開くときに、初期化イベントを発生させるようにするキー。  
  
    > [!NOTE]  
    >  ドキュメントまたはブックを開いた場合、 **Getting Started**を押し、作業ウィンドウ**Shift**コードをバイパスしていません。 また、shift キーを押しができないイベントが、ドキュメントを開いた後に発生します。  
  
     このメソッドは、変更を加えるコードを実行していると、文書の変更がないドキュメントを開きたい場合に便利です。  
  
## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>アセンブリをバイパスするには、名前を変更または削除するのには  
  
-   アセンブリが配置されているコンピューターで必要なアクセス許可があれば、名前を変更または文書またはブックが見つけられないため、アセンブリを削除できます。 Office ドキュメントが開かれるたびに発生するエラーが発生します。  
  
     複数の人が、ソリューションを使用する場合、このメソッドは、それらのすべての実行から、ソリューションを防ぎます。 これは、コードまたは参照先のサーバーで問題が見つかるし、実行のすべてのユーザーを停止する場合に役立ちます。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティで保護された Office ソリューション](../vsto/securing-office-solutions.md)   
 [Office ソリューションをデプロイします。](../vsto/deploying-an-office-solution.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Office ソリューションにおけるアプリケーションと配置マニフェスト](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  