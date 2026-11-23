Title: What the IndiaAI compute numbers count

[Read HTML](https://rawthoughts.in/collections/ideas/india-ai/what-the-compute-numbers-count/)

Author: Harsh Joshi

<a id="what-the-indiaai-compute-numbers-count"></a>

# What the IndiaAI compute numbers count

In two official August 2026 accounts, the same 237 projects and 93.18 lakh GPU-hours occupied different positions in the story. One described approved projects and sanctioned hours. The other described projects that had accessed subsidised computing. A change in the verb can sound like a change in delivery, even when the number stays the same.

This investigation follows programme reports and allocation-register observations through 24 September 2026. It asks a narrow question: what can those public records establish about the conversion of promised compute into useful work? The observation period matters because a later consumption report could answer a question these records leave open.

<a id="the-verb-changes-the-event"></a>

## The verb changes the event

The [6 August parliamentary answer](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2295477) reports 237 projects approved for subsidised support and 93.18 lakh GPU-hours sanctioned. The [13 August factsheet](https://www.pib.gov.in/FactsheetDetails.aspx?Id=150860) calls the same figures accessed compute. It separately reports 62 prototypes and 20 deployed solutions. Neither supplies a project-level reconciliation connecting those hours to those outputs.

Approval can establish eligibility for support. Sanction can establish an allocation. Access can mean that an applicant has a usable route into the service. Consumption would record actual use. An output would identify what that use produced. These events can occur close together, but no arithmetic lets one count substitute for the others without knowing the reporting definition.

The question is consequential for a buyer or programme operator. If an allocation expires before a workload starts, the approved hours did not become consumed hours. If a run starts and repeatedly fails, consumption can increase without a usable model or completed experiment. Conversely, a small efficient run can produce valuable output with fewer hours. A favourable count at one stage can accompany very different outcomes at the next.

<a id="a-start-by-date-is-an-obligation"></a>

## A start-by date is an obligation

The [compute portal's allocation register](https://compute.indiaai.gov.in/endusers), observed on 3 and 24 September, provided columns for applicants, providers, allocated equipment, project duration, allocation dates and start-by dates. With project rows, those fields would identify who received an award and when use was expected to begin. The observed columns did not report consumed hours, expiry, queueing, service reliability, completion or attributable output for the same projects.

The seven user-category counters summed to 301 on 3 September and 304 on 24 September: two more Startups & MSMEs and one more Early-stage startup. Those are changes in the portal’s user counters, not a consumption series or a reconciliation of the 237 projects. The saved calculation below compares the counters, the allocation fields and the two August reports. Both captured tables retain their headings but no project rows; those were requested separately by the page. The dated responses needed to match individual projects are missing.

The client script used a `startusedate` field to populate the start-by column. A field name alone cannot establish that a workload actually started. The public presentation has to tell us which event is being recorded.

An [allocation service-level commitment](https://compute.indiaai.gov.in/sla) also answers a narrower question than a workload guarantee. Promising to allocate a request within a stated window does not establish uninterrupted execution or completion by a customer's deadline. [The capacity promise needs its own clock](https://rawthoughts.in/collections/useful-compute/a-capacity-promise-needs-a-clock/): when the job can start, what happens after an interruption and which remedy applies if the window is missed.

<a id="one-provider-s-trace-from-allocated-compute-to-released-models"></a>

## One provider's trace from allocated compute to released models

The evidence is not all unresolved allocation. In its [6 March model release](https://www.sarvam.ai/blogs/sarvam-30b-105b), Sarvam says it trained its 30B and 105B models in India on IndiaAI compute, released their weights and put them into production services. Its earlier [Indus launch](https://www.sarvam.ai/blogs/introducing-indus) described limited-beta access and a waitlist under constrained compute capacity.

That account connects supplied compute to identifiable model artifacts and services, while also showing that service access can remain constrained after the model exists. It is a provider's account of particular outputs, not an independently reconciled conversion rate for all programme-supported projects. It nevertheless prevents the national argument from collapsing into “nothing was delivered.” Some useful work can be visible while the portfolio-wide denominator remains unresolved.

<a id="the-strongest-alternative-is-reporting-lag"></a>

## The strongest alternative is reporting lag

Perhaps the sanctioned hours had already become real use, and “accessed” was a reasonable shorthand for that transition. Perhaps the prototypes and deployments were early results that simply had not been joined to the compute register publicly. That would be a reporting gap rather than a delivery failure. The absence of the join cannot decide which explanation is right.

A useful next table would follow the same supported project cohort from approved or sanctioned hours into started and consumed hours, expired or cancelled allocations, service performance, completed work and output identifiers. It would state the observation interval and define the stages. Projects whose completion takes longer should remain visible as continuing work rather than disappear from the denominator.

That table could change the conclusion in either direction. Reliable conversion within the promised windows would show that the administrative counts are a useful leading account of delivery. Large non-starts or repeated interruption would reveal where the bridge is failing. Without it, the figures establish support and access more clearly than the rate at which that support becomes completed work.

[The physical chain](https://rawthoughts.in/collections/ideas/india-ai/testing-indias-ai-crossing/from-posters-to-throughput/) explains what makes usable compute possible. The reporting chain has to connect that possibility to an actual workload. Neither a national GPU count nor a suspicious reading of a headline can finish the investigation on its own.


## Article notes



<a id="gazette-notebook-4d156600173f692076d2865e643c2666544999b27c74daa7dc733c8c75d80e15--cell-0-comparing-the-indiaai-register-observations"></a>

## Comparing the IndiaAI register observations

The August reports repeat 237 projects and 93.18 lakh GPU-hours, with different verbs. The September register observations let us examine the allocation register a month later. Do they supply the project-level connection between those claims?

The inputs below come from the dated public sources linked with each record. Category values are the HTML counters’ `data-purecounter-end` attributes; subsidy is the integer rupee value in the subsidy field. The complete `enduserTable` element is included, shared here because it is identical in both captures. Hashes identify the complete saved source files, not the live pages or these excerpts. This notebook uses Python’s standard library and makes no network requests.

Sources: [6 August parliamentary answer](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2295477), [13 August factsheet](https://www.pib.gov.in/FactsheetDetails.aspx?Id=150860), [allocation register](https://compute.indiaai.gov.in/endusers) and [its client script](https://compute.indiaai.gov.in/js/common/endusers.js). The last two links identify the source locations; their live contents may differ from the September observations.

Execution count: 1

```python
from decimal import Decimal
from html.parser import HTMLParser
import re

registers = [{'observed': '2026-09-03',
  'url': 'https://compute.indiaai.gov.in/endusers',
  'capture_sha256': 'e6b21a3d8eab3374afb00c2e9c7de628be893f69df90ead06a21001435cef102',
  'user_category_counters': {'Researchers or Academia': 31,
                             'Startups & MSMEs': 65,
                             'IndiaAI Fellowship': 1,
                             'Students': 19,
                             'Early-stage startup': 40,
                             'Early-stage researchers': 5,
                             'Govt entities': 140},
  'subsidy_rupees': 12744176729,
  'subsidy_container_class': 'col-md-4 d-none'},
 {'observed': '2026-09-24',
  'url': 'https://compute.indiaai.gov.in/endusers',
  'capture_sha256': '16b6250d540595efe425002e6391385afac995e26f32960187fc0299af48cb2a',
  'user_category_counters': {'Researchers or Academia': 31,
                             'Startups & MSMEs': 67,
                             'IndiaAI Fellowship': 1,
                             'Students': 19,
                             'Early-stage startup': 41,
                             'Early-stage researchers': 5,
                             'Govt entities': 140},
  'subsidy_rupees': 12752471056,
  'subsidy_container_class': 'col-md-4 d-none'}]

official_reports = [{'published': '2026-08-06',
  'url': 'https://www.pib.gov.in/PressReleasePage.aspx?PRID=2295477&lang=1&reg=1',
  'capture_sha256': 'c4f40c7e9e27ac0cb2074d5a532bbe52fcba6ad3af6fe5fc3fc45c814feba6dc',
  'excerpt': '237 projects have been approved for subsidized compute support, with '
             '93.18 lakh GPU hours sanctioned.'},
 {'published': '2026-08-13',
  'url': 'https://www.pib.gov.in/FactsheetDetails.aspx?ModuleId=16&NoteId=150860&id=150860&lang=1&reg=46',
  'capture_sha256': 'a0cb49cd1b8f8e1a0713452fab2986ffda53fe31e20730b88135940629ed27f9',
  'excerpt': 'By August 2026, 237 projects had accessed subsidised AI computing, '
             'covering 93.18 lakh GPU hours.'}]

register_table_html = """<table id="enduserTable" class="table table-bordered yr-table dataTable display nowrap">
                                <thead>
                                    <tr>
                                        <th>SNo.</th>
                                        <th>Allocation date</th>
                                        <th>Name of Applicant</th>
                                        <th>Organisation</th>
                                        <th>No. of GPUs</th>
                                        <th>Type of GPUs</th>
                                        <th>Service provider</th>
                                        <th>User Category</th>
                                        <th>Subsidy Allocated</th>
                                        <th>Bill of Materials</th>
                                        <th>Project Duration</th>
                                        <th>Date by which applicant must start using</th>
                                    </tr>
                                </thead>
                            </table>"""

client_script = {'observed': '2026-09-24',
 'url': 'https://compute.indiaai.gov.in/js/common/endusers.js',
 'capture_sha256': 'b4eb58d6c07e2697f05b8b659496f3e0403db8bc54be44706cf176447e86be53'}
client_script["request_excerpt"] = """url: getContextPath() + "/enduserDashboardData",
        type: "POST","""
client_script["columns_excerpt"] = """columns: [
                    { data: null },
                    {
                        data: "approveddate",
                        render: data => data ? data.replace("T", " ") : ""
                    },
                    { data: "name" },
                    { data: "organizationname" },
                    {
                        data: "total_number_of_gpu",
                        render: data => data ? data : 0
                    },
                    { data: "gpu_types" },
                    { data: "csp" },
                    { data: "usertype" },
                    {
                        data: "subsidyallocated",
                        render: data => data && !data.toString().trim().startsWith("₹") ? `₹${data}` : data
                    },
                    {
                        data: "totalprice",
                        render: data => data && !data.toString().trim().startsWith("₹") ? `₹${data}` : data
                    },
                    {
                        data: null,
                        render: (data, type, row) => {
                            const formatDate = dateStr => dateStr ? dateStr.replace("T", " ").replaceAll("-", "/") : "";
                            return `${formatDate(row.projectstartdate)} - ${formatDate(row.projectenddate)}`;
                        }
                    },
                    { data: "startusedate" },
                ]"""
```

<a id="gazette-notebook-4d156600173f692076d2865e643c2666544999b27c74daa7dc733c8c75d80e15--cell-2-what-stayed-the-same-in-august"></a>

### What stayed the same in August

These are reported aggregate figures. Matching their values is a useful comparison of the wording; it does not establish the identity or progress of each project.

Execution count: 2

```python
def table(headers, rows):
    rows = [[str(value) for value in row] for row in rows]
    widths = [max(len(headers[i]), *(len(row[i]) for row in rows)) for i in range(len(headers))]
    print("  ".join(value.ljust(widths[i]) for i, value in enumerate(headers)))
    print("  ".join("-" * width for width in widths))
    for row in rows:
        print("  ".join(value.ljust(widths[i]) for i, value in enumerate(row)))

reported = []
for report in official_reports:
    text = report["excerpt"]
    projects = int(re.search(r"(\d+) projects", text).group(1))
    hours = int(Decimal(re.search(r"([\d.]+) lakh GPU hours", text).group(1)) * 100_000)
    event = "approved / sanctioned" if "sanctioned" in text else "accessed"
    reported.append((report["published"], projects, hours, event))
assert reported[0][1:3] == reported[1][1:3]
table(["Report date", "Projects", "GPU-hours", "Reported event"], reported)
```

stdout

```
Report date  Projects  GPU-hours  Reported event       
-----------  --------  ---------  ---------------------
2026-08-06   237       9318000    approved / sanctioned
2026-08-13   237       9318000    accessed             
```

<a id="gazette-notebook-4d156600173f692076d2865e643c2666544999b27c74daa7dc733c8c75d80e15--cell-4-what-changed-in-the-register"></a>

### What changed in the register

The portal calls these user-category counters. Their sum is kept separate from the August project count. The subsidy value is present in a container marked `d-none`, so this comparison is of the saved HTML field, not a claim that the page displayed it to visitors.

Execution count: 3

```python
earlier, later = registers
assert earlier["user_category_counters"].keys() == later["user_category_counters"].keys()
rows = []
for category, first in earlier["user_category_counters"].items():
    second = later["user_category_counters"][category]
    rows.append((category, first, second, f"{second - first:+d}"))
sums = [sum(record["user_category_counters"].values()) for record in registers]
rows.append(("Sum of category counters", *sums, f"{sums[1] - sums[0]:+d}"))
table(["User category", "3 Sep", "24 Sep", "Change"], rows)

print()
rupees = [record["subsidy_rupees"] for record in registers]
table(["Observation", "Subsidy field (rupees)", "Crore rupees"], [
    (record["observed"], f"{record['subsidy_rupees']:,}", f"{Decimal(record['subsidy_rupees']) / 10_000_000:.7f}")
    for record in registers
])
print(f"Change in subsidy field: {rupees[1] - rupees[0]:,} rupees")
```

stdout

```
User category             3 Sep  24 Sep  Change
------------------------  -----  ------  ------
Researchers or Academia   31     31      +0    
Startups & MSMEs          65     67      +2    
IndiaAI Fellowship        1      1       +0    
Students                  19     19      +0    
Early-stage startup       40     41      +1    
Early-stage researchers   5      5       +0    
Govt entities             140    140     +0    
Sum of category counters  301    304     +3    

Observation  Subsidy field (rupees)  Crore rupees
-----------  ----------------------  ------------
2026-09-03   12,744,176,729          1274.4176729
2026-09-24   12,752,471,056          1275.2471056
Change in subsidy field: 8,294,327 rupees
```

<a id="gazette-notebook-4d156600173f692076d2865e643c2666544999b27c74daa7dc733c8c75d80e15--cell-6-what-a-start-by-column-establishes"></a>

### What a start-by column establishes

The table heading names a deadline: “Date by which applicant must start using.” In the saved client script, the last column uses `startusedate`. Its name does not change the displayed deadline into a measured workload start. The other columns describe the applicant and allocation, rather than consumed hours or completed work.

Execution count: 4

```python
class RegisterTable(HTMLParser):
    def __init__(self):
        super().__init__()
        self.headings = []
        self.current_heading = None
        self.current_cells = None
        self.data_rows = 0
    def handle_starttag(self, tag, attrs):
        if tag == "tr":
            self.current_cells = 0
        elif tag == "th":
            self.current_heading = []
        elif tag == "td" and self.current_cells is not None:
            self.current_cells += 1
    def handle_data(self, text):
        if self.current_heading is not None:
            self.current_heading.append(text)
    def handle_endtag(self, tag):
        if tag == "th":
            self.headings.append(" ".join("".join(self.current_heading).split()))
            self.current_heading = None
        elif tag == "tr":
            if self.current_cells:
                self.data_rows += 1
            self.current_cells = None

parsed = RegisterTable()
parsed.feed(register_table_html)
for number, heading in enumerate(parsed.headings, start=1):
    print(f"{number:2}. {heading}")
fields = re.findall(r'data:\s*"([^"]+)"', client_script["columns_excerpt"])
assert fields[-1] == "startusedate"
assert len(parsed.headings) == 12
print("\nLast column's client field:", fields[-1])
print("Project data rows preserved in each captured table:", parsed.data_rows)
print("Project rows requested separately from: /enduserDashboardData (POST)")
```

stdout

```
 1. SNo.
 2. Allocation date
 3. Name of Applicant
 4. Organisation
 5. No. of GPUs
 6. Type of GPUs
 7. Service provider
 8. User Category
 9. Subsidy Allocated
10. Bill of Materials
11. Project Duration
12. Date by which applicant must start using

Last column's client field: startusedate
Project data rows preserved in each captured table: 0
Project rows requested separately from: /enduserDashboardData (POST)
```

<a id="gazette-notebook-4d156600173f692076d2865e643c2666544999b27c74daa7dc733c8c75d80e15--cell-8-the-missing-comparison"></a>

### The missing comparison

The seven category counters total **301 and 304**; they are not a reconciliation of the reported **237 projects**. The complete saved register table contains headings but no project records. Those rows were requested separately by the client script, and the corresponding dated responses are not available in these inputs. A zero row count here describes the capture, not zero allocations or zero activity.

The notebook therefore cannot calculate how many of the 237 projects started, how many sanctioned hours were consumed or what they produced. That requires the membership of the reported cohort and project-level records linking allocations to actual use and outputs over a stated interval. Reporting lag remains a possible explanation; these observations do not establish a delivery failure.





Reading path: [Ideas](https://rawthoughts.in/collections/ideas/) > [India's AI crossing](https://rawthoughts.in/collections/ideas/india-ai/) > [What the IndiaAI compute numbers count](https://rawthoughts.in/collections/ideas/india-ai/what-the-compute-numbers-count/)
