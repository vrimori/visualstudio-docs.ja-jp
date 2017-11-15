---
title: "方法: ビルドからプロジェクトを除外する | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64a10c356100e6ace36ec1c574c85479741113c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-exclude-projects-from-a-build"></a>方法: ビルドからプロジェクトを除外する
ソリューションをビルドするために、含まれるすべてのプロジェクトをビルドする必要はありません。 たとえば、ビルドを中断するプロジェクトを除外できます。 その後、問題の調査と対処を行ってからプロジェクトをビルドすることができます。  
  
 次の方法を実行することでプロジェクトを除外できます。  
  
-   アクティブなソリューション構成からプロジェクトを一時的に削除する。  
  
-   対象プロジェクトを含まないソリューション構成を作成する。  
  
 詳しくは、「[ビルド構成について](../ide/understanding-build-configurations.md)」をご覧ください。  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>アクティブなソリューション構成からプロジェクトを一時的に削除するには  
  
1.  メニュー バーで **[ビルド]**、 **[構成マネージャー]**の順に選択します。  
  
2.  **[プロジェクトのコンテキスト]** テーブルで、ビルドから除外するプロジェクトを見つけます。  
  
3.  プロジェクトの **[ビルド]** 列で、チェック ボックスをオフにします。  
  
4.  **[閉じる]** を選択し、ソリューションをリビルドします。  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>プロジェクトを除外するソリューション構成を作成するには  
  
1.  メニュー バーで **[ビルド]**、 **[構成マネージャー]**の順に選択します。  
  
2.  **[アクティブ ソリューション構成]** 一覧の **[\<新規作成>]** を選択します。  
  
3.  **[名前]** ボックスに、ソリューション構成の名前を入力します。  
  
4.  **[設定のコピー元]** ボックスの一覧で、新しい構成のベースにするソリューション構成 (**[デバッグ]** など) を選択し、**[OK]** を選択します。  
  
5.  **[構成マネージャー]** ダイアログ ボックスで、除外するプロジェクトの **[ビルド]** 列のチェック ボックスをオフにし、**[閉じる]** を選択します。  
  
6.  **[標準]** ツール バーで、**[ソリューション構成]** ボックスのアクティブな構成が、新しいソリューション構成であることを確認します。  
  
7.  メニュー バーから、**[ビルド]**、**[ソリューションのリビルド]** の順に選びます。  
  
## <a name="see-also"></a>関連項目  
 [ビルド構成について](../ide/understanding-build-configurations.md)   
 [方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)   
 [方法: 複数の構成を同時にビルドする](../ide/how-to-build-multiple-configurations-simultaneously.md)