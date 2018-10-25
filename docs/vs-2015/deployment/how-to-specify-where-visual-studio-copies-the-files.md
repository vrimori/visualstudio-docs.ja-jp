---
title: '方法: Visual Studio がファイルをコピーする場所の指定 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 6661eeeeaa802e482dd540f7a7793186f917edf3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853806"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>方法: Visual Studio がファイルをコピーする場所を指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce を使用してアプリケーションを発行する場合、`Publish Location` プロパティによってアプリケーション ファイルとマニフェストが配置される場所が指定されます。 これには、ファイル パスまたは FTP サーバーへのパスを指定できます。  
  
 指定できます、`Publish Location`プロパティを**発行**のページ、**プロジェクト デザイナー**、または発行ウィザードを使用しています。 詳細については、次を参照してください。[方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)します。  
  
> [!NOTE]
>  ClickOnce を使用してアプリケーションの複数のバージョンをインストールすると、以前のバージョンのアプリケーションは、指定した発行場所の Archive というフォルダーに移されます。 以前のバージョンがこのようにアーカイブされることで、インストール ディレクトリが以前のバージョンのフォルダーから分離されます。  
  
### <a name="to-specify-a-publishing-location"></a>発行場所を指定するには  
  
1. **ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **発行**タブをクリックします。  
  
3. **発行場所**フィールドに、次の形式のいずれかを使用して、発行場所を入力します。  
  
   - にファイル共有またはディスク パスを発行するには、UNC パスを使用してパスを入力 (\\\Server\ApplicationName) またはファイル パス (C:\Deploy\ApplicationName)。  
  
   - FTP サーバーを発行するには、ftp://ftp.microsoft.com/ApplicationName という形式を使用して、パスを入力します。  
  
     テキスト内に存在する必要があります、**発行場所**ボックスに、参照ボタン (**.**) ボタンが機能します。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションの発行](../deployment/publishing-clickonce-applications.md)   
 [方法: 発行ウィザードを使用して ClickOnce アプリケーションを発行する](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



