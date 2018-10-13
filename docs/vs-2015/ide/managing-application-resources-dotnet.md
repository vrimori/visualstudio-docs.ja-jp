---
title: アプリケーション リソースの管理 (.NET) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- editors [Visual Studio], Resource Designer
- Resource Designer
- resources [Visual Studio], managing
- Resources page in Project Designer
- resources types, Resource Designer
- application resources [Visual Studio]
- Project Designer, Resources page
ms.assetid: f2582734-8ada-4baa-8a7c-e2ef943ddf7e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b29f32fa59f719af3efab6901596b682c95a5d57
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287223"
---
# <a name="managing-application-resources-net"></a>アプリケーション リソースの管理 (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

リソース ファイルとは、アプリケーションの一部ですが、コンパイルされないファイルのことであり、たとえばアイコン ファイルやオーディオ ファイルが該当します。 これらのファイルはコンパイル処理の一部ではないため、バイナリを再コンパイルする必要なしで変更することができます。 アプリケーションをローカライズすることを計画している場合は、アプリケーションをローカライズするときに変更する必要があるすべての文字列とその他のリソースに関して、リソース ファイルを使用する必要があります。  
  
 .NET デスクトップ アプリ内のリソースの詳細については、「[デスクトップ アプリケーションのリソース](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)」を参照してください。 C++ デスクトップ アプリ内でのリソースの詳細については、「 [Working with Resource Files](http://msdn.microsoft.com/library/2699a539-b369-4b78-80f0-df03eb7b6780)」を参照してください。  
  
 Windows ストア アプリは、デスクトップ アプリとは異なる別のリソース モデルを使用します。 Windows ストア アプリ内のリソースの詳細については、Windows デベロッパー センター Web サイトの「 [アプリケーション リソースの定義](https://msdn.microsoft.com/library/windows/apps/hh465228.aspx) 」を参照してください。  
  
## <a name="working-with-resources"></a>リソースの操作  
 マネージド コード プロジェクト内で、プロジェクトのプロパティ ウィンドウを開くために、 **ソリューション エクスプローラー** でプロジェクト ノードを右クリックして **[プロパティ]** をクリックするか、 **[クイック起動]** ウィンドウに **プロジェクトのプロパティ** を入力するか、 **ソリューション エクスプローラー** ウィンドウ内で Alt キーを押しながら Enter キーを押します。 **[リソース]** タブをクリックします。プロジェクトにまだ .resx ファイルが含まれていない場合や、異なる種類のリソースを追加および削除する場合、また既存のリソースを変更する場合は、.resx ファイルを追加できます。  
  
 C++ プロジェクトでのリソースの操作方法については、「[方法: リソースを作成する](http://msdn.microsoft.com/library/aad44914-9145-45a3-a7d8-9de89b366716)」を参照してください。

