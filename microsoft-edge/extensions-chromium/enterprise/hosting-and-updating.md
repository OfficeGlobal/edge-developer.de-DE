---
description: Erweiterungen Enterprise-Dokumentation für Edge (Chrom)-Erweiterungen.
title: Hosten und aktualisieren
author: MSEdgeTeam
ms.author: msedgedevrel
ms.date: 12/05/2019
ms.topic: article
ms.prod: microsoft-edge-chromium
keywords: Edge-Chromium, Erweiterungen-Entwicklung, Browser-Erweiterungen, Addons, Partner Center, Entwickler
ms.openlocfilehash: eb1f9921d503d25557fc9efb1517537e7a90f4aa
ms.sourcegitcommit: 6860234c25a8be863b7f29a54838e78e120dbb62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2020
ms.locfileid: "10567515"
---
# <span data-ttu-id="e8057-104">Web Store-Hosting und-Aktualisierung</span><span class="sxs-lookup"><span data-stu-id="e8057-104">Web Store Hosting and Updating</span></span>  

<span data-ttu-id="e8057-105">Die meisten Erweiterungen werden im [Microsoft Edge Insider Addons-Katalog (Microsoft Edge Insider Addons \)][MicrosoftStoreExtensions] gehostet, um Benutzer am besten vor böswilligen Erweiterungen zu schützen.</span><span class="sxs-lookup"><span data-stu-id="e8057-105">Most Extensions are hosted in the [Microsoft Edge Insider Addons catalog \(Microsoft Edge Insider Addons\)][MicrosoftStoreExtensions] to best protect users from malicious Extensions.</span></span>  

## <span data-ttu-id="e8057-106">Hosting</span><span class="sxs-lookup"><span data-stu-id="e8057-106">Hosting</span></span>  

<span data-ttu-id="e8057-107">Alle Erweiterungen werden als spezielle ZIP-Datei mit dem Suffix ". Wagon" an die Benutzer verteilt.</span><span class="sxs-lookup"><span data-stu-id="e8057-107">All Extensions are distributed to users as a special ZIP file with a .crx suffix.</span></span>  <span data-ttu-id="e8057-108">Erweiterungen, die in Microsoft Edge-Addons gehostet werden, werden als ZIP-Dateien hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="e8057-108">Extensions hosted in the Microsoft Edge Addons are uploaded as .zip files.</span></span> <span data-ttu-id="e8057-109">Der Veröffentlichungsprozess wandelt die ZIP-Datei automatisch in eine ".".</span><span class="sxs-lookup"><span data-stu-id="e8057-109">The publishing process automatically converts the .zip into a .crx file.</span></span>  

<span data-ttu-id="e8057-110">Es gibt zwei Ausnahmen von der Hosting-Regel für Microsoft Edge-Add-ons:</span><span class="sxs-lookup"><span data-stu-id="e8057-110">There are two exceptions to the Microsoft Edge Addons hosting rule:</span></span>  

1.  <span data-ttu-id="e8057-111">Erweiterungen, die über die Unternehmensrichtlinie verteilt werden.</span><span class="sxs-lookup"><span data-stu-id="e8057-111">Extensions that are distributed through the Enterprise policy.</span></span>  
1.  <span data-ttu-id="e8057-112">Degepackte Erweiterungs Verzeichnisse von einem lokalen Computer im Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="e8057-112">Unpacked Extension directories from a local machine while in developer mode.</span></span>  

## <span data-ttu-id="e8057-113">Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="e8057-113">Updating</span></span>  

<span data-ttu-id="e8057-114">Der Microsoft Edge-Browser überprüft in regelmäßigen Abständen nach neuen Versionen installierter Erweiterungen und Updates ohne Benutzereingriff.</span><span class="sxs-lookup"><span data-stu-id="e8057-114">The Microsoft Edge browser periodically checks for new versions of installed Extensions and updates each without user intervention.</span></span>  

> [!NOTE]
> <span data-ttu-id="e8057-115">Es werden Schritte zum Aktualisieren einer Erweiterung auf Microsoft Edge-Addons geplant, die hinzugefügt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="e8057-115">Steps to update an Extension on Microsoft Edge Addons are planned be added.</span></span>  

<!-- image links -->

<!-- links -->  

[MicrosoftStoreExtensions]: https://microsoftedge.microsoft.com/insider-addons/category/EdgeExtensions "Erweiterungen – Microsoft Edge Insider-Addons"  

> [!NOTE]
> <span data-ttu-id="e8057-117">Teile dieser Seite sind Änderungen, die auf der [von Google erstellten und freigegebenen][GoogleSitePolicies] Arbeit basieren und gemäß den in der [Creative Commons Attribution 4,0 International-Lizenz][CCA4IL]beschriebenen Begriffen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e8057-117">Portions of this page are modifications based on work created and [shared by Google][GoogleSitePolicies] and used according to terms described in the [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  
> <span data-ttu-id="e8057-118">Die ursprüngliche Seite finden Sie [hier](https://developer.chrome.com/extensions/hosting).</span><span class="sxs-lookup"><span data-stu-id="e8057-118">The original page is found [here](https://developer.chrome.com/extensions/hosting).</span></span>  

[![Creative Commons-Lizenz][CCby4Image]][CCA4IL]  
<span data-ttu-id="e8057-120">Diese Arbeit unterliegt einer [Creative Commons Attribution 4.0 International License][CCA4IL].</span><span class="sxs-lookup"><span data-stu-id="e8057-120">This work is licensed under a [Creative Commons Attribution 4.0 International License][CCA4IL].</span></span>  

[CCA4IL]: https://creativecommons.org/licenses/by/4.0  
[CCby4Image]: https://i.creativecommons.org/l/by/4.0/88x31.png  
[GoogleSitePolicies]: https://developers.google.com/terms/site-policies  