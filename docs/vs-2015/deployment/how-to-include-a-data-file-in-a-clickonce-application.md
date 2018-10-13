---
title: '方法: ClickOnce アプリケーションにデータ ファイルを含める |Microsoft Docs'
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
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 5e954550b8d59f1d1672e1229387714ad251a38c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204699"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>方法 : ClickOnce アプリケーションにデータ ファイルを含める
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

各[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーションをインストールするには、アプリケーションが独自のデータを管理できる先のコンピューターのローカル ディスク上のデータ ディレクトリが割り当てられます。 データ ファイルは、任意の種類のファイルを含めることができます。 テキスト ファイル、XML ファイル、または偶数の Microsoft Access データベース (.mdb) ファイル。 次の手順に任意の型のデータ ファイルを追加する方法を示して、[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]アプリケーション。  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Mage.exe を使用して、データ ファイルを追加するには  
  
1.  アプリケーションのファイルの残りの部分で、アプリケーション ディレクトリにデータ ファイルを追加します。  
  
     通常、アプリケーションのディレクトリは、展開の現在のバージョン ラベルが付いた、ディレクトリに — v1.0.0.0 など。  
  
2.  データ ファイルの一覧に、アプリケーション マニフェストを更新します。  
  
     **mage-u v1.0.0.0\Application.manifest-fromdirectory v1.0.0.0**  
  
     このタスクを実行すると、アプリケーション マニフェストでファイルの一覧を再作成しも自動的にハッシュ署名を生成します。  
  
3.  任意のテキスト エディターまたは XML エディターで、アプリケーション マニフェストを開き、検索、`file`最近追加されたファイルの要素。  
  
     という XML ファイルを追加する場合は`Data.xml`ファイルは次のコード例のようになります。  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  属性を追加`type`この要素の値を入力して`data`します。  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  証明書またはキー ペアを使用して、アプリケーション マニフェストに再署名し、配置マニフェストを再署名します。  
  
     アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
     **mage-s アプリ マニフェストの cf cert_file-pwd パスワード**  
  
     **mage-u 配置マニフェスト appm アプリ マニフェスト**  
  
     **mage-s 配置マニフェストは、cf certfile-pwd パスワード**  
  
2.  
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>MageUI.exe を使用してデータ ファイルを追加するには  
  
1.  アプリケーションのファイルの残りの部分で、アプリケーション ディレクトリにデータ ファイルを追加します。  
  
2.  通常、アプリケーションのディレクトリは、展開の現在のバージョン ラベルが付いた、ディレクトリに — v1.0.0.0 など。  
  
3.  **ファイル** メニューのをクリックして**開く**をアプリケーション マニフェストを開きます。  
  
4.  選択、**ファイル**タブ。  
  
5.  タブの上部にあるテキスト ボックスで、アプリケーションのファイルを含むディレクトリを入力し、クリックして**Populate**します。  
  
     データ ファイルは、グリッドに表示されます。  
  
6.  設定、**ファイルの種類**データ ファイルの値**データ**します。  
  
7.  アプリケーション マニフェストを保存し、ファイルを再署名します。  
  
     MageUI.exe は、ファイルを再度署名することを求められます。  
  
8.  配置マニフェストに再署名します。  
  
     アプリケーション マニフェストのハッシュが変更されたため、配置マニフェストを再署名する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ClickOnce アプリケーションにおけるローカル データおよびリモート データへのアクセス](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)



