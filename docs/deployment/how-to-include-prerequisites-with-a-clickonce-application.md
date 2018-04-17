---
title: '方法: ClickOnce アプリケーションと共に必須コンポーネントを含める |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 7283ce590770c1ed2d14ffb79ec71d594c8b21f1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>方法 : ClickOnce アプリケーションと共に必須コンポーネントを含める
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] アプリケーションと共に必須コンポーネントを配布する前に、まず開発用コンピューターにそれらの必須コンポーネントのインストーラー パッケージをダウンロードする必要があります。 アプリケーションの発行を選択して**マイ アプリケーションと同じ場所から必須コンポーネントをダウンロード**、インストーラー パッケージがない場合、エラーが発生、**パッケージ**フォルダーです。  
  
> [!NOTE]
>  .NET Framework のインストーラー パッケージを追加するを参照してください。[開発者にとっての .NET Framework 配置ガイド](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)です。  
  
##  <a name="Package"></a> Package.xml を使用してインストーラー パッケージを追加するには  
  
1.  ファイル エクスプ ローラーで、開く、**パッケージ**フォルダーです。  
  
     既定では、パスは 32 ビット システムでは C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages、64 ビット システムでは C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages です。  
  
2.  必須コンポーネントを追加するのフォルダーを開き、インストールされているバージョンの言語のフォルダーを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)](たとえば、 **en**英語の場合)。  
  
3.  メモ帳で開き、 **Package.xml**ファイル。  
  
4.  検索、**名**を含む要素**http://go.microsoft.com/fwlink**URL をコピーします。 含める、 **LinkID**部分。  
  
    > [!NOTE]
    >  ない場合は**名前**要素が含まれます **http://go.microsoft.com/fwlink**を開き、 **Product.xml**の前提条件のルート フォルダー内のファイルを見つけて選択、 **fwlink**文字列。  
  
    > [!IMPORTANT]
    >  一部の必須コンポーネントには、複数のインストーラー パッケージ (たとえば、32 ビット システム用または 64 ビット システム用) があります。 複数**名前**要素を含む**fwlink**、それぞれの残りの手順を繰り返す必要があります。  
  
5.  ブラウザーのアドレス バーに URL を貼り付け、実行または保存するメッセージが表示されたら、**保存**です。  
  
     この手順では、コンピューターにインストーラー ファイルをダウンロードします。  
  
6.  必須コンポーネントのルート フォルダーにファイルをコピーします。  
  
     たとえば、Windows Installer 4.5 の前提条件の場合は、\Packages\WindowsInstaller 4_5 フォルダーにファイルをコピーします。  
  
     これで、アプリケーションと共にインストーラー パッケージを配布できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)